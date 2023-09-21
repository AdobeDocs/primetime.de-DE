---
description: Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Implementieren eines benutzerdefinierten Inhaltsauflösers {#implement-a-custom-content-resolver}

Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.

Wenn TVSDK eine neue Chance generiert, iteriert es durch die registrierten Content-Resolver, die nach einer suchen, die in der Lage ist, diese Gelegenheit zu lösen. Die erste, die `true` ausgewählt wird, um die Gelegenheit zu lösen. Wenn kein Content Resolver in der Lage ist, wird diese Möglichkeit übersprungen. Da die Inhaltsauflösung normalerweise asynchron erfolgt, ist der Content Resolver für die Benachrichtigung von TVSDK verantwortlich, wenn der Prozess abgeschlossen ist.

1. Eigene benutzerdefinierte Implementierung `ContentFactory`, indem die `ContentFactory` Benutzeroberfläche und Überschreiben `retrieveResolvers`.

   Beispiel:

   ```java
   class MyContentFactory extends ContentFactory { 
       @Override 
       public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { 
           List<ContentResolver> resolvers = new ArrayList<ContentResolver>(); 
           MediaPlayerItemConfig itemConfig = item.getConfig(); 
           if(itemConfig) { 
               CustomRangeMetadata customRanges = itemConfig.getCustomRangeMetadata(); 
               if (customRanges) { 
                   List<ReplaceTimeRange> timeRanges = customRanges.getTimeRangeList(); 
   
                   if (timeRanges && timeRanges.size() > 0) 
                   { 
                   // CustomRangeResolver is only activated by the presence of CustomRanges in configuration 
                   resolvers.add(new CustomRangeResolver()); 
                   } 
               } 
               AdvertisingMetadata metadata = itemConfig.getAdvertisingMetadata(); 
               if (metadata) { 
                   if (metadata instanceOf AuditudeSettings)  
                       resolvers.add(new AuditudeResolver(getContext());    
                   } 
               } 
           // add your custom resolver if any 
           resolvers.add(MyOpportunityGenerator(item)); 
           return resolvers; 
       } 
       ... 
   } 
   ```

1. Registrieren `ContentFactory` der `MediaPlayer`.

   Beispiel:

   ```java
   //Register the custom content factory with the media player 
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new MyContentFactory()); 
   
   //Pass this config while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config); 
   
   // OR use MediaPlayerItemLoader to pre-load a resource 
   id = 23; 
   itemLoader.load(resource, id, config);
   ```

1. Übergeben eines `AdvertisingMetadata` -Objekt auf TVSDK wie folgt fest:
   1. Erstellen Sie eine `AdvertisingMetadata` -Objekt.
   1. Speichern Sie die `AdvertisingMetadata` Objekt zu `MediaPlayerItemConfig`.

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. Erstellen Sie eine benutzerdefinierte Anzeigenauflöser-Klasse, die die `ContentResolver` -Klasse.
   1. Überschreiben Sie im benutzerdefinierten Anzeigenauflöser `doConfigure`, `doCanResolve`, `doResolve`, `doCleanup`:

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      Sie erhalten Ihre `advertisingMetadata` aus dem übergebenen Element `doConfigure`:

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. Erstellen Sie für jede Platzierungsmöglichkeit eine `List<TimelineOperation>`.

      Dieses Beispiel `TimelineOperation` bietet eine Struktur für `AdBreakPlacement`:

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. Rufen Sie nach Auflösung der Anzeigen eine der folgenden Funktionen auf:

      * Wenn die Anzeigenauflösung erfolgreich ist, rufen Sie auf `process(List<TimelineOperation> proposals)` und `notifyCompleted(Opportunity opportunity)` auf `ContentResolverClient`

        ```java
        _client.process(timelineOperations); 
        _client.notifyCompleted(opportunity); 
        ```

      * Wenn die Anzeigenauflösung fehlschlägt, rufen Sie auf `notifyResolveError` auf `ContentResolverClient`

        ```java
        _client.notifyFailed(Opportunity opportunity, PSDKErrorCode error);
        ```

        Beispiel:

        ```java
        _client.notifyFailed(opportunity, UNSUPPORTED_OPERATION);
        ```

<!--<a id="example_463B718749504A978F0B887786844C39"></a>-->

Mit diesem benutzerdefinierten Beispiel-Anzeigenauflöser wird eine Chance gelöst und eine einfache Anzeige bereitgestellt:

```java
public class CustomContentResolver extends ContentResolver { 
    protected void doConfigure(MediaPlayerItem item){} 
 
    protected boolean doCanResolve(Opportunity opportunity) {  
        return true;  
    } 
 
    protected void doResolve(Opportunity opportunity) { 
        _client.process(createAdBreakPlacementsFor(opportunity.getPlacement())); 
        _client.notifyCompleted(opportunity); 
    } 
 
    private List<TimelineOperation> createAdBreakPlacementsFor(Placement placementInformation) { 
        List<Ad> ads = new ArrayList<Ad>(); 
        AdAsset adAsset = new AdAsset("101", 15000, new MediaResource( 
          "https: . . ..m3u8", MediaResource.Type.HLS, null), null, null); 
 
        Ad ad = Ad.linearFromAsset("101", adAsset, null, null, false); 
        ads.add(ad); 
        AdBreak adBreak = new AdBreak(ads, null, AdInsertionType.CLIENT_INSERTED); 
 
        List<TimelineOperation> result = new ArrayList<TimelineOperation>(); 
 
        result.add(new AdBreakPlacement(placementInformation, adBreak)); 
        return result; 
    } 
 
    protected void doCleanup() {} 
} 
```
