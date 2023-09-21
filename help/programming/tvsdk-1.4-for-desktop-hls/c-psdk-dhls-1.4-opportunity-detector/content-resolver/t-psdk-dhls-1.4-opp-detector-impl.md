---
description: Sie können Ihre eigenen Opportunitäts-Detektoren implementieren.
title: Implementieren eines benutzerdefinierten Opportunity-Detektors
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Implementieren eines benutzerdefinierten Opportunity-Detektors{#implement-a-custom-opportunity-detector}

Sie können Ihre eigenen Opportunitäts-Detektoren implementieren.

* Wenn Ihr Opportunity-Generator auf `TimedMetadata` Objekte, die mit dem aktuellen Medien-Stream verknüpft sind, sollten Sie dann die `SpliceOutOpportunityGenerator` oder `TimedMetadataOpportunityGenerator`.

* Wenn Ihr Opportunity-Generator auf Out-of-Band-Daten basiert, die von einem externen Dienst (z. B. einem CIS) bereitgestellt werden, sollte der `OpportunityGenerator`.

1. Erstellen Sie den benutzerdefinierten Opportunity-Generator.

       Wenn Ihr benutzerdefinierter Opportunity-Generator auf &quot;TimedMetadata&quot;-Objekten basiert, erweitern Sie &quot;TimedMetadataOpportunityGenerator&quot;und überschreiben Sie diese Methoden:
   
   * `doConfigure` - Diese Methode wird aufgerufen, nachdem das Medienplayer-Element erstellt wurde, und bietet dem Opportunity-Generator die Möglichkeit, bei Bedarf einen anfänglichen Satz von Möglichkeiten zu erstellen
   * `doProcess` - Diese Methode wird jedes Mal aufgerufen, wenn neue `TimedMetadata` erkannt wird (z. B. bei Live-/linearen Streams, sobald die Wiedergabeliste/das Manifest aktualisiert wird)

   ```
   public class CustomOpportunityGenerator extends TimedMetadataOpportunityGenerator { 
       override protected function doConfigure(playhead:Number, playbackRange:TimeRange):void { 
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadataCollection:Vector.<TimedMetadata> = item.timedMetadata; 
       } 
   
       override protected function doProcess(timedMetadata:TimedMetadata):void { 
           ... 
   
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve(opportunity); 
       }  
       ... 
   }
   ```

1. Erstellen Sie die benutzerdefinierte Inhaltsfactory, die den benutzerdefinierten Opportunity-Generator verwendet.

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       ... 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
           var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
           result.push(new CustomOpportunityGenerator()); 
   
           return result; 
       } 
   }
   ```

1. Registrieren Sie die benutzerdefinierte Inhaltsfactory für die Wiedergabe des Medien-Streams.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
