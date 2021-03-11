---
description: Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 2%

---


# Implementieren eines benutzerdefinierten Inhaltsauflösers {#implement-a-custom-content-resolver}

Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.

Wenn TVSDK eine neue Chance generiert, durchläuft es die registrierten Content-Auflöser, die nach einer suchen, die in der Lage ist, diese Gelegenheit zu lösen. Das erste, das `true` zurückgibt, wird ausgewählt, um die Gelegenheit zu lösen. Wenn kein Inhaltsauflöser geeignet ist, wird diese Gelegenheit übersprungen. Da die Inhaltsauflösung normalerweise asynchron abläuft, ist der Content-Auflöser dafür verantwortlich, TVSDK zu benachrichtigen, wenn der Prozess abgeschlossen ist.

1. Implementieren Sie Ihre eigene benutzerdefinierte `ContentFactory`, indem Sie die `ContentFactory`-Schnittstelle erweitern und `retrieveResolvers` überschreiben.

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

1. Registrieren Sie `ContentFactory` auf `MediaPlayer`.

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

1. Übergeben Sie ein `AdvertisingMetadata`-Objekt wie folgt an TVSDK:
   1. Erstellen Sie ein `AdvertisingMetadata`-Objekt.
   1. Speichern Sie das `AdvertisingMetadata`-Objekt in `MediaPlayerItemConfig`.

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. Erstellen Sie eine benutzerdefinierte Anzeigenauflösungsklasse, die die `ContentResolver`-Klasse erweitert.
   1. Überschreiben Sie im benutzerdefinierten Anzeigenauflöser `doConfigure`, `doCanResolve`, `doResolve`, `doCleanup`:

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      Sie erhalten Ihr `advertisingMetadata`-Element aus dem Element, das in `doConfigure` übergeben wird:

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. Erstellen Sie für jede Platzierungsmöglichkeit ein `List<TimelineOperation>`.

      Dieses Beispiel `TimelineOperation` stellt eine Struktur für `AdBreakPlacement` bereit:

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. Rufen Sie nach Auflösung der Anzeigen eine der folgenden Funktionen auf:

      * Wenn die Anzeigenauflösung erfolgreich ist, rufen Sie `process(List<TimelineOperation> proposals)` und `notifyCompleted(Opportunity opportunity)` auf die `ContentResolverClient`

         ```java
         _client.process(timelineOperations); 
         _client.notifyCompleted(opportunity); 
         ```

      * Wenn die Anzeigenauflösung fehlschlägt, rufen Sie `notifyResolveError` auf dem `ContentResolverClient` auf

         ```java
         _client.notifyFailed(Opportunity opportunity, PSDKErrorCode error);
         ```

         Beispiel:

         ```java
         _client.notifyFailed(opportunity, UNSUPPORTED_OPERATION);
         ```

<!--<a id="example_463B718749504A978F0B887786844C39"></a>-->

Mit diesem Beispiel-benutzerdefinierten Anzeigenauflöser wird eine Gelegenheit gelöst und eine einfache Anzeige bereitgestellt:

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

