---
description: Ein MediaPlayer-Objekt kapselt das Verhalten und die Funktionalität eines Medienplayers.
title: MediaPlayer einrichten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---


# MediaPlayer{#set-up-the-mediaplayer} einrichten

Ein MediaPlayer-Objekt kapselt das Verhalten und die Funktionalität eines Medienplayers.

1. Instanziieren Sie ein `MediaPlayer` mit folgendem Code:

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Erstellen Sie eine `MediaPlayerView`-Instanz:

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   wobei `container` das Element der Zielgruppe `div` ist, das Ihr `HTMLMediaElement` enthält.

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

1. Hängen Sie die `MediaPlayerView`-Instanz an Ihre `MediaPlayer`-Instanz an:

   ```js
   player.view = view;
   ```

1. Fügen Sie die benutzerdefinierten Steuerelemente `div` an Ihre MediaPlayer-Instanz an.

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

Die `MediaPlayer`-Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
