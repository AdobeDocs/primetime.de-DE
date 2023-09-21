---
description: Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Implementieren eines benutzerdefinierten Inhaltsauflösers{#implement-a-custom-content-resolver}

Sie können Ihre eigenen Content Resolver basierend auf den Standard-Resolver implementieren.

Wenn Browser TVSDK eine neue Chance erkennt, durchläuft es die registrierten Content-Resolver, die nach einer suchen, die in der Lage ist, diese Gelegenheit mithilfe der `canResolve` -Methode. Die erste, die &quot;true&quot;zurückgibt, wird ausgewählt, um die Gelegenheit zu lösen. Wenn kein Content Resolver in der Lage ist, wird diese Möglichkeit übersprungen. Da die Inhaltsauflösung normalerweise asynchron erfolgt, ist der Inhaltsauflöser für die Benachrichtigung des Browser TVSDK verantwortlich, wenn der Prozess abgeschlossen ist.

Beachten Sie die folgenden Informationen:

* Die Aufrufe des Content Resolver `client.process` um anzugeben, welcher Timeline-Vorgang von TVSDK ausgeführt werden muss.

  Der Vorgang ist normalerweise eine Platzierung von Werbeunterbrechungen.

* Die Aufrufe des Content Resolver `client.notifyCompleted` wenn der Auflösungsprozess erfolgreich ist oder `client.notifyFailed` , wenn der Prozess fehlschlägt.

1. Erstellen Sie einen benutzerdefinierten Opportunity-Resolver.

   ```js
   /** 
     * Class implementing AdobePSDK.ContentResolver interface  
   */ 
   CustomResolver = function () { 
   }; 
   
   CustomResolver.prototype = { 
       constructor: CustomResolver, 
       configureCallbackFunc: function (item, client) { 
       // here you can read any media stream characteristics which 
       // might help configure your content resolver like 
       // - the media player item configuration through the item.config 
       // - the media resource metadata through item.resource.metadata 
      }, 
   
       canResolveCallbackFunc: function (opportunity) { 
       // check if the opportunity can be resolved by this resolver 
       // if yes return true, otherwise return false 
       return true; 
      }, 
   
       resolveCallbackFunc: function (opportunity) {         
       // start the resolving process 
       // communicate with your custom ad server 
   
       // in this example we assume that: 
       // - if successful, onResolveCompleted method will be invoked 
       // - if failed, onResolveFailed method will be invoked 
      }, 
   
       onResolveCompleted: function (response) { 
        try { 
           var proposals = []; 
           // extract the timeline ad placement from the response 
           // and add them to the proposal vector 
           // - extract the ad break 
           // - calculate the placement (can reuse the _opportunity.placement) 
           // var timelineOperation = new AdobePSDK.AdBreakPlacement (adBreak, placement); 
           // proposals.push (timelineOperation); 
   
           client.process (proposals); 
           client.notifyCompleted (_opportunity); 
       } catch (error) { 
           onResolveFailed (error); 
       } 
   }, 
   
       onResolveFailed: function (error) { 
         client.notifyFailed (_opportunity); 
       } 
   
   }; 
   ```

1. Erstellen Sie die benutzerdefinierte Inhaltsfactory, die den benutzerdefinierten Inhaltsauflöser verwendet.

   Beispiel:

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
       constructor: CustomContentFactory, 
       retrieveResolversCallbackFunc: function (item) { 
           var result = []; 
           var resource = item.resource; 
           if (resource.metadata.containsKey("custom-opportunity-detector")) { 
               result.push (new CustomResolver()); 
           } 
           return result; 
       }, 
       … 
   }; 
   ```

1. Registrieren Sie die benutzerdefinierte Inhaltsfactory für die Wiedergabe des Medien-Streams.

   Im UI Framework-Player können Sie die benutzerdefinierte Inhaltsfactory wie folgt angeben:

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var advertisingMetadata = new AdobePSDK.AdvertisingMetadata(); 
   // set any parameter you need for custom ad resolver 
   // advertisingMetadata.setValue ("customparam", "customvalue"); 
   
   var metadata = new AdobePSDK.Metadata(); 
   metadata.setMetadata ("custom-opportunity-detector", advertisingMetadata); 
   
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
       mediaPlayerItemConfig: { 
              advertisingFactory: advertisingFactory 
       }, 
          mediaResource: { 
                  resourceUrl:'Specify Resource Url', 
                  metadata: metadata 
          } 
   } 
   
   }); 
   ```
