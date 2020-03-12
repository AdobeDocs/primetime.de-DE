---
description: Ein MediaPlayer-Objekt kapselt das Verhalten und die Funktionalität eines Medienplayers.
seo-description: Ein MediaPlayer-Objekt kapselt das Verhalten und die Funktionalität eines Medienplayers.
seo-title: MediaPlayer einrichten
title: MediaPlayer einrichten
uuid: 2279e388-6fbc-49a2-8560-218d3d31e1d6
translation-type: tm+mt
source-git-commit: af9b865bc1627a97bf8957b5460ff9b46052a7dc

---


# MediaPlayer einrichten{#set-up-the-mediaplayer}

Ein MediaPlayer-Objekt kapselt das Verhalten und die Funktionalität eines Medienplayers.

1. Instanziieren einer `MediaPlayer` Datei mit den folgenden Methoden:

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Erstellen Sie eine `MediaPlayerView` Instanz:

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   wobei `container` das Element Zielgruppe `div` ist, das Ihre `HTMLMediaElement`.

   Beispiel:

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

1. Fügen Sie Ihre `MediaPlayerView` Instanz an Ihre `MediaPlayer` Instanz an:

   ```js
   player.view = view;
   ```

1. Schließen Sie das Element für benutzerdefinierte Steuerelemente `div` an Ihre MediaPlayer-Instanz an.

   In HTML:

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

Die `MediaPlayer` Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
