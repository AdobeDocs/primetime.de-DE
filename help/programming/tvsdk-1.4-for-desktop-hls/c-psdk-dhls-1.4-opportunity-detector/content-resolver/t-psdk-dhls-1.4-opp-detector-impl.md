---
description: Sie können eigene Opportunitätsdetektoren implementieren.
seo-description: Sie können eigene Opportunitätsdetektoren implementieren.
seo-title: Implementieren eines benutzerdefinierten Opportunitätsdetektors
title: Implementieren eines benutzerdefinierten Opportunitätsdetektors
uuid: 18fb431b-4585-4293-92a7-b77ab7f9b7db
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Implementieren eines benutzerdefinierten Opportunitätsdetektors{#implement-a-custom-opportunity-detector}

Sie können eigene Opportunitätsdetektoren implementieren.

* Wenn Ihr Opportunitätsgenerator auf `TimedMetadata` Objekten basiert, die mit dem aktuellen Medienstream verknüpft sind, sollte er die Erweiterung `SpliceOutOpportunityGenerator` oder `TimedMetadataOpportunityGenerator`.

* Wenn Ihr Opportunitätsgenerator auf Out-of-Band-Daten basiert, die von einem externen Dienst (z. B. einem CIS) bereitgestellt werden, sollte er den `OpportunityGenerator`Vorgang erweitern.

1. Erstellen Sie den benutzerdefinierten Opportunitätsgenerator.

       Wenn Ihr benutzerdefinierter Opportunity-Generator auf &quot;TimedMetadata&quot;-Objekten basiert, erweitern Sie &quot;TimedMetadataOpportunityGenerator&quot; und überschreiben Sie diese Methoden:
   
   * `doConfigure` - Diese Methode wird aufgerufen, nachdem das Medienplayer-Element erstellt wurde und bietet dem Medienplayer die Möglichkeit, bei Bedarf eine Reihe anfänglicher Möglichkeiten zu erstellen.
   * `doProcess` - Diese Methode wird jedes Mal aufgerufen, wenn neue Funktionen erkannt `TimedMetadata` werden (z. B. bei Live-/linearen Streams bei jeder Aktualisierung der Playlist/des Manifests)

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

1. Erstellen Sie die benutzerdefinierte Inhaltsfabrik, die den benutzerdefinierten Opportunitätsgenerator verwendet.

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

1. Registrieren Sie die benutzerdefinierte Inhaltsfactory für den wiederzugebenden Medienstream.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

