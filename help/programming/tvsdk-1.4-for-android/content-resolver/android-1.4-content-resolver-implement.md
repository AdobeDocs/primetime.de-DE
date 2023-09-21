---
description: Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Implementieren eines benutzerdefinierten Inhaltsauflösers {#implement-a-custom-content-resolver}

Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.

Wenn TVSDK eine neue Chance erkennt, durchläuft es die registrierten Content-Resolver, die nach einer suchen, die diese Gelegenheit lösen kann. Die erste, die &quot;true&quot;zurückgibt, wird ausgewählt, um die Gelegenheit zu lösen. Wenn kein Content Resolver in der Lage ist, wird diese Möglichkeit übersprungen. Da die Inhaltsauflösung normalerweise asynchron abläuft, ist der Inhaltsauflöser dafür verantwortlich, darüber zu informieren, wann der Prozess abgeschlossen ist.

1. Benutzerdefiniert erstellen `AdvertisingFactory` Instanz und Überschreibung `createContentResolver`.

   Beispiel:

   ```java
   new AdvertisingFactory() { 
       ... 
       @Override 
       public ContentResolver createContentResolver(MediaPlayerItem item) { 
           Metadata metadata = _mediaPlayer.getCurrentItem().getResource().getMetadata(); 
           if (metadata != null) { 
               if (metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue())) { 
                   return new AuditudeResolver(getActivity().getApplicationContext()); 
               } else if (metadata.containsKey(DefaultMetadataKeys.JSON_METADATA_KEY.getValue())) { 
                   return new MetadataResolver(); 
               } else if (metadata.containsKey(DefaultMetadataKeys.TIME_RANGES_METADATA_KEY.getValue())) { 
                   return new CustomAdMarkersContentResolver(); 
               } else if (metadata.containsKey(CustomAdResolver.CUSTOM_METADATA_KEY)) { 
                   return new CustomAdResolver(); 
               } 
           } 
           return null; 
       } 
       ... 
   }
   ```

1. Registrieren Sie die Client-Factory der Anzeige bei der `MediaPlayer`.

   Beispiel:

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Übergeben eines `AdvertisingMetadata` -Objekt auf TVSDK wie folgt fest:
   1. Erstellen Sie eine `AdvertisingMetadata` Objekt und `MetadataNode` -Objekt.
   1. Speichern Sie die `AdvertisingMetadata` Objekt zu `MetadataNode`.

   ```java
   MetadataNode result = new MetadataNode(); 
   result.setNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue(),  
                  advertisingMetadata);
   ```

1. Erstellen Sie eine benutzerdefinierte Anzeigenauflöser-Klasse, die die `ContentResolver` -Klasse.
   1. Überschreiben Sie im benutzerdefinierten Anzeigenauflöser diese geschützte Funktion:

      ```java
      void doResolveAds(Metadata metadata,  
                        PlacementOpportunity placementOpportunity)
      ```

      Metadaten enthalten Ihre `AdvertisingMetada`. Verwenden Sie ihn für Folgendes `TimelineOperation` Vektorgenerierung.

   1. Erstellen Sie für jede Platzierungsmöglichkeit eine `Vector<TimelineOperation>`.

      Der Vektor kann leer, aber nicht null sein.

      Dieses Beispiel `TimelineOperation` bietet eine Struktur für `AdBreakPlacement`:

      ```java
      AdBreakPlacement(AdBreak.createAdBreak( 
                                ads,       // Vector<Ad> 
                                time,      // Ad Break start time. Note: local time on the timeline 
                                duration,  // Ad Break duration 
                                tag()      // An arbitrary string value that can be attached to  
                                           // the AdBreak object. 
                               ), placementInformation  // Retrieved from PlacementOpportunity 
      )
      ```

   1. Rufen Sie nach Auflösung der Anzeigen eine der folgenden Funktionen auf:

      * Wenn die Anzeigenauflösung erfolgreich ist: `notifyResolveComplete(Vector<TimelineOperation> proposals)`
      * Wenn die Anzeigenauflösung fehlschlägt: `notifyResolveError(Error error)`

      Wenn dies beispielsweise fehlschlägt:

      ```java
      Metadata metadata = new MetadataNode(); 
      metadata.setValue("NATIVE_ERROR_CODE", exception.getCause().toString()); 
      error.setMetadata(metadata);
      ```

<!--<a id="example_4F0D7692A92E480A835D6FDBEDBE75E7"></a>-->

Dieser benutzerdefinierte Beispiel-Anzeigenauflöser sendet eine HTTP-Anfrage an den Anzeigenserver und erhält eine JSON-Antwort.

```java
public class CustomAdResolver extends ContentResolver { 
    ... 
    @Override 
    protected void doResolveAds(Metadata metadata, PlacementOpportunity placementOpportunity) { 
        ... 
        if (resolveSuccess == true) { 
            notifyResolveComplete(Vector<TimelineOperation> proposals); 
        } 
        else { 
            notifyResolveError(Error error); 
        } 
    } 
    ... 
}
```

Beispiel-JSON-Anzeigenserver-Antwort für einen Live-Stream:

```
{     
    "response": { 
        "breaks": [ { 
            "start": 0, 
            "ads": [ { 
                "id": 1001, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/geico/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset1", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } 
        ] }, 
        { 
            "start": -1, 
            "ads": [ { 
                "id": 1003, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/priceline/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset3", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        } ] 
    } 
} 
```

Beispiel für eine JSON-Anzeigenserverantwort für VOD:

```
{     
    "response": { 
        "breaks": [ { 
            "start": 0, 
            "ads": [ { 
                "id": 1001, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/geico/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset1", 
                    "resource_type": "" 
                }, 
                "companion_assets": {  
                } 
            }, 
            { 
                "id": 1002, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/crescent/playlist.m3u8", 
                    "duration": 15000, 
                    "id": "asset2", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        }, 
        { 
            "start": 50000, 
            "ads": [ { 
                "id": 1003, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/priceline/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset3", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        }, 
        { 
            "start": 100000000, 
            "ads": [ { 
                "id": 1004, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/camry/playlist.m3u8", 
                    "duration": 15000, 
                    "id": "asset4", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        } ] 
    } 
} 
```
