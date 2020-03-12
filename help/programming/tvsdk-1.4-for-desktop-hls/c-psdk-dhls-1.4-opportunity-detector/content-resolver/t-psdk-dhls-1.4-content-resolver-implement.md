---
description: Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.
seo-description: Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.
seo-title: Implementieren eines benutzerdefinierten Inhaltsauflösers
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
uuid: 1714fcd9-45e0-48be-97f3-f702265128a4
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Implementieren eines benutzerdefinierten Inhaltsauflösers{#implement-a-custom-content-resolver}

Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.

Wenn TVSDK eine neue Chance erkennt, durchläuft es die registrierten Content-Auflöser, die nach einer suchen, die diese Gelegenheit mit der `canResolve` Methode lösen kann. Das erste, das &quot;true&quot;zurückgibt, wird ausgewählt, um die Gelegenheit zu lösen. Wenn kein Inhaltsauflöser geeignet ist, wird diese Gelegenheit übersprungen. Da die Inhaltsauflösung normalerweise asynchron abläuft, ist der Content-Auflöser dafür verantwortlich, TVSDK zu benachrichtigen, wenn der Prozess abgeschlossen ist.

* Der Content-Auflöser ruft `client.place` auf, um anzugeben, welche Zeitschienen-Operation TVSDK ausgeführt werden muss (üblicherweise eine Platzierung von Werbeunterbrechungen).
* Der Inhaltsauflöser ruft auf, `client.notifyCompleted` wenn der Auflösungsprozess erfolgreich ist oder `client.notifyFailed` wenn der Prozess fehlschlägt.

1. Erstellen Sie einen benutzerdefinierten Opportunitätsauflöser.

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

1. Registrieren Sie die benutzerdefinierte Inhaltsfactory für den wiederzugebenden Medienstream.

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

