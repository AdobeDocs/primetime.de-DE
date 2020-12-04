---
description: Sie können Ihren eigenen Opportunity Generator implementieren, indem Sie die OpportunityGenerator-Schnittstelle erweitern.
seo-description: Sie können Ihren eigenen Opportunity Generator implementieren, indem Sie die OpportunityGenerator-Schnittstelle erweitern.
seo-title: Implementieren eines benutzerdefinierten Opportunitätsgenerators
title: Implementieren eines benutzerdefinierten Opportunitätsgenerators
uuid: b80da2da-32d5-41f7-86ca-936d6f25b015
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 4%

---


# Implementieren eines benutzerdefinierten Opportunitätsgenerators{#implement-a-custom-opportunity-generator}

Sie können Ihren eigenen Opportunity Generator implementieren, indem Sie die OpportunityGenerator-Schnittstelle erweitern.

1. Erstellen Sie den benutzerdefinierten Opportunitätsgenerator.

   Beispiel:

   ```js
   /** 
   * Class implementing AdobePSDK.OpportunityGenerator interface 
   */ 
   CustomOpportunityGenerator = function () { 
   }; 
   
   CustomOpportunityGenerator.prototype = { 
       constructor: CustomOpportunityGenerator, 
       configureCallbackFunc: function (item, client, mode, playhead, playbackRange) {  
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current AdobePSDK.MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadatas = item.timedMetadata; 
       }, 
       updateCallbackFunc: function (playhead, playbackRange) { 
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve (opportunity); 
       }, 
       … 
   }; 
   ```

1. Erstellen Sie die benutzerdefinierte Inhaltsfabrik, die den benutzerdefinierten Opportunitätsgenerator verwendet.

   Beispiel:

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
          constructor: CustomContentFactory, 
          retrieveOpportunityGeneratorsCallbackFunc: function (item) { 
               var result = []; 
               result.push (new CustomOpportunityGenerator()); 
               return result; 
       }, 
       … 
   }; 
   ```

1. Registrieren Sie die benutzerdefinierte Inhaltsfactory für den wiederzugebenden Medienstream.

   Im UI-Framework-Player können Sie die Factory für benutzerdefinierte Inhalte wie folgt festlegen:

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
           mediaPlayerItemConfig: { 
                   advertisingFactory: advertisingFactory 
           }, 
               mediaResource: { 
                   resourceUrl:'Specify Resource Url' 
          } 
     } 
   }); 
   ```

