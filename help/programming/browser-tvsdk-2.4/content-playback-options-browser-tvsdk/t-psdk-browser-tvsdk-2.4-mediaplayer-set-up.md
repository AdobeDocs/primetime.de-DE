---
description: Ein MediaPlayer-Objekt kapselt das Verhalten und die Funktionalität eines Medienplayers.
title: MediaPlayer einrichten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# MediaPlayer einrichten{#set-up-the-mediaplayer}

Ein MediaPlayer-Objekt kapselt das Verhalten und die Funktionalität eines Medienplayers.

1. Instanziieren eines `MediaPlayer` Verwenden Sie Folgendes:

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Erstellen Sie eine `MediaPlayerView` instance:

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   where `container` ist die Zielgruppe `div` -Element enthält, das `HTMLMediaElement`.

   Beispielsweise auf einer HTML-Seite:

   ```
   <div id="videoDiv"> 
   <codeph>
     <div id="video-controls"> 
          ... custom video controls 
     </div> 
   </codeph> 
   </div>
   ```

   Aufruf:

   ```js
   var view = new  
   <codeph>
   AdobePSDK.MediaPlayerView 
   </codeph>( 
         document.getElementById("videoDiv"));  
   ```

1. Anhängen Ihrer `MediaPlayerView` -Instanz zu Ihrer `MediaPlayer` instance:

   ```js
   player.view = view;
   ```

1. Anfügen der benutzerdefinierten Steuerelemente `div` -Element zu Ihrer MediaPlayer-Instanz hinzufügen.

   Beispiel für HTML:

   ```
   <div id="videoDiv"> 
      <div id="video-controls"> 
         ..... custom video controls 
      </div> 
   </div>
   ```

   Aufruf:

   ```js
   if (typeof player.getView() !== 'undefined') { 
       var view = player.view; 
       view.attachVideoControls(document.getElementById("video-controls")); 
   }
   ```

Die `MediaPlayer` -Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
