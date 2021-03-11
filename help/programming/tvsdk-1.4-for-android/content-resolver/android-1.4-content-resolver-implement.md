---
description: Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---


# Implementieren eines benutzerdefinierten Inhaltsauflösers {#implement-a-custom-content-resolver}

Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.

Wenn TVSDK eine neue Gelegenheit erkennt, durchläuft es die registrierten Content-Auflöser, die nach einer suchen, die diese Gelegenheit lösen kann. Das erste, das &quot;true&quot;zurückgibt, wird ausgewählt, um die Gelegenheit zu lösen. Wenn kein Inhaltsauflöser geeignet ist, wird diese Gelegenheit übersprungen. Da die Inhaltsauflösung in der Regel asynchron abläuft, ist der Inhaltsauflöser dafür verantwortlich, benachrichtigt zu werden, wenn der Prozess abgeschlossen ist.

1. Erstellen Sie eine benutzerdefinierte `AdvertisingFactory`-Instanz und überschreiben Sie `createContentResolver`.

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

1. Registrieren Sie die Client-Factory der Anzeige bei `MediaPlayer`.

   Beispiel:

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Übergeben Sie ein `AdvertisingMetadata`-Objekt wie folgt an TVSDK:
   1. Erstellen Sie ein `AdvertisingMetadata`-Objekt und ein `MetadataNode`-Objekt.
   1. Speichern Sie das `AdvertisingMetadata`-Objekt in `MetadataNode`.

   ```java
   MetadataNode result = new MetadataNode(); 
   result.setNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue(),  
                  advertisingMetadata);
   ```

1. Erstellen Sie eine benutzerdefinierte Anzeigenauflösungsklasse, die die `ContentResolver`-Klasse erweitert.
   1. Überschreiben Sie im benutzerdefinierten Anzeigenauflöser diese geschützte Funktion:

      ```java
      void doResolveAds(Metadata metadata,  
                        PlacementOpportunity placementOpportunity)
      ```

      Metadaten enthalten Ihr `AdvertisingMetada`. Verwenden Sie sie für die folgende Vektorgenerierung `TimelineOperation`.

   1. Erstellen Sie für jede Platzierungsmöglichkeit ein `Vector<TimelineOperation>`.

      Der Vektor kann leer, jedoch nicht null sein.

      Dieses Beispiel `TimelineOperation` stellt eine Struktur für `AdBreakPlacement` bereit:

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

      * Bei erfolgreicher Anzeigenauflösung: `notifyResolveComplete(Vector<TimelineOperation> proposals)`
      * Wenn die Anzeigenauflösung fehlschlägt: `notifyResolveError(Error error)`

      Wenn dies z. B. fehlschlägt:

      ```java
      Metadata metadata = new MetadataNode(); 
      metadata.setValue("NATIVE_ERROR_CODE", exception.getCause().toString()); 
      error.setMetadata(metadata);
      ```


<!--<a id="example_4F0D7692A92E480A835D6FDBEDBE75E7"></a>-->

Dieser benutzerdefinierte Beispiel-Anzeigenauflöser sendet eine HTTP-Anforderung an den Anzeigenserver und empfängt eine JSON-Antwort.

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

Beispiel-JSON-Anzeigenserverantwort für einen Live-Stream:

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

Beispiel-JSON-Anzeigenserverantwort für VOD:

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

