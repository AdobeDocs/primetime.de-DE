---
description: Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.
seo-description: Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.
seo-title: Implementieren eines benutzerdefinierten Inhaltsauflösers
title: Implementieren eines benutzerdefinierten Inhaltsauflösers
uuid: cf85dd90-242e-4f9e-9785-158ca0fc9465
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Implementieren eines benutzerdefinierten Inhaltsauflösers{#implement-a-custom-content-resolver}

Sie können Ihre eigenen Inhaltsauflöser auf Basis der Standardauflöser implementieren.

Wenn Browser TVSDK eine neue Gelegenheit erkennt, durchläuft es die registrierten Content-Auflöser, die nach einer Lösung suchen, die diese Möglichkeit mithilfe der `canResolve` Methode lösen kann. Das erste, das &quot;true&quot;zurückgibt, wird ausgewählt, um die Gelegenheit zu lösen. Wenn kein Inhaltsauflöser geeignet ist, wird diese Gelegenheit übersprungen. Da die Inhaltsauflösung normalerweise asynchron abläuft, ist der Inhaltsauflöser dafür verantwortlich, Browser TVSDK zu benachrichtigen, wenn der Prozess abgeschlossen ist.

Beachten Sie die folgenden Informationen:

* Der Inhaltsauflöser ruft `client.process` auf, um anzugeben, welche Zeitschiene von TVSDK ausgeführt werden muss.

   Der Vorgang ist in der Regel eine Platzierung von Werbeunterbrechungen.

* Der Inhaltsauflöser ruft auf, `client.notifyCompleted` wenn der Auflösungsprozess erfolgreich ist oder `client.notifyFailed` wenn der Prozess fehlschlägt.

1. Erstellen Sie einen benutzerdefinierten Opportunitätsauflöser.

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

1. Registrieren Sie die benutzerdefinierte Inhaltsfactory für den wiederzugebenden Medienstream.

   Im UI Framework-Player können Sie die Factory für benutzerdefinierte Inhalte wie folgt festlegen:

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

