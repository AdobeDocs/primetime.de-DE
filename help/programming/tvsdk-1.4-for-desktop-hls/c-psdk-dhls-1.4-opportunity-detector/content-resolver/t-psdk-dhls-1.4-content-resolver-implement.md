---
description: Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Implementieren eines benutzerdefinierten Inhaltsauflösers{#implement-a-custom-content-resolver}

Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.

Wenn TVSDK eine neue Chance erkennt, durchläuft es die registrierten Content-Resolver, die nach einer suchen, die in der Lage ist, diese Gelegenheit mithilfe der `canResolve` -Methode . Die erste, die &quot;true&quot;zurückgibt, wird ausgewählt, um die Gelegenheit zu lösen. Wenn kein Content Resolver in der Lage ist, wird diese Möglichkeit übersprungen. Da die Inhaltsauflösung normalerweise asynchron erfolgt, ist der Content Resolver für die Benachrichtigung von TVSDK verantwortlich, wenn der Prozess abgeschlossen ist.

* Die Aufrufe des Content Resolver `client.place` um anzugeben, welche Timeline-Operation TVSDK ausführen muss (normalerweise eine Platzierung von Werbeunterbrechungen).
* Die Aufrufe des Content Resolver `client.notifyCompleted` wenn der Auflösungsprozess erfolgreich ist, oder `client.notifyFailed` , wenn der Prozess fehlschlägt.

1. Erstellen Sie einen benutzerdefinierten Opportunity-Resolver.

   ```
   public class CustomResolver extends ContentResolver { 
   
       /** 
        * Default constructor. 
        */ 
       public function CustomResolver() { 
       } 
   
       override protected function doConfigure(item:MediaPlayerItem):void { 
           // here you can read any media stream characteristics which 
           // might help configure your content resolver like 
           // - the media player item configuration through the item.config 
           // - the media resource metadata through item.resource.metadata 
       } 
   
       /** 
        * @inheritDoc 
        */ 
       override protected function doCanResolve(opportunity:Opportunity):Boolean { 
           // check if the opportunity can be resolved by this resolver 
           // if yes return true, otherwise return false 
   
           return true; 
       } 
   
       /** 
        * @inheritDoc 
        */ 
       override protected function doResolve(opportunity:Opportunity):void { 
           // start the resolving process 
           // communicate with your custom ad server 
   
           // in this example we assume that: 
           // - if successful, onResolveCompleted method will be invoked 
           // - if failed, onResolveFailed method will be invoked 
       } 
   
       private function onResolveCompleted(response:*):void { 
           try { 
               var proposals:Vector.<TimelineOperation> = new Vector.<TimelineOperation>(); 
   
               // extract the timeline ad placement from the response 
               // and add them to the proposal vector 
               // - extract the ad break 
               // - calculate the placement ( can reuse the opportunity.placement ) 
               // var timelineOperation:AdBreakPlacement = new AdBreakPlacement(placement, adBreak); 
               // proposals.push(timelineOperation); 
   
               client.process(proposals); 
               client.notifyCompleted(_opportunity); 
           } catch (error:Error) { 
               onResolveFailed(error); 
           } 
       } 
   
       private function onResolveFailed(error:Error):void { 
   
           var errorMetadata:Metadata = new Metadata(); 
           MetadataUtils.serializeError(error, errorMetadata); 
   
           var mediaError:MediaError = new MediaError(NotificationCode.CONTENT_RESOLVING_ERROR, errorMetadata); 
           client.notifyFailed(_opportunity, mediaError); 
       } 
   
       ... 
   }
   ```

1. Erstellen Sie die benutzerdefinierte Inhaltsfactory, die den benutzerdefinierten Inhaltsauflöser verwendet.

   Beispiel:

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
           ... 
   
           /** 
            * @inheritDoc 
            */ 
           override protected function  
             doRetrieveResolvers(item:MediaPlayerItem):Vector.<ContentResolver> { 
               var result:Vector.<ContentResolver> = new Vector.<ContentResolver>(); 
   
               var resource:MediaResource = item.resource; 
   
               if (resource.metadata != null) { 
                   if (resource.metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY)) { 
                       result.push(new AuditudeAdResolver()); 
                   } else if (resource.metadata.containsKey("custom-opportunity-detector")) { 
                       result.push(new CustomResolver()); 
                   } 
               } 
               return result; 
           } 
   }
   ```

1. Registrieren Sie die benutzerdefinierte Inhaltsfactory für die Wiedergabe des Medien-Streams.

   Beispiel:

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   var advertisingMetadata:AdvertisingMetadata = new AdvertisingMetadata(); 
   // set any parameter you need for custom ad resolver 
   // advertisingMetadata.setValue("customparam", "customvalue"); 
   
   var metadata:Metadata = new Metadata(); 
   metadata.setMetadata("custom-opportunity-detector", advertisingMetadata); 
   var mediaResource:MediaResource = MediaResource.createFromUrl(url, metadata);
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
