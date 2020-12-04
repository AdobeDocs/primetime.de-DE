---
description: Führen Sie die folgenden Schritte aus, um einen einfachen Player mit dem Browser TVSDK zu erstellen.
seo-description: Führen Sie die folgenden Schritte aus, um einen einfachen Player mit dem Browser TVSDK zu erstellen.
seo-title: Erstellen eines einfachen Players mit TVSDK
title: Erstellen eines einfachen Players mit TVSDK
uuid: ec15cf53-197f-4190-a6b2-600a57815390
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Erstellen eines einfachen Players mit TVSDK{#create-a-basic-player-using-tvsdk}

Führen Sie die folgenden Schritte aus, um einen einfachen Player mit dem Browser TVSDK zu erstellen.

1. Erstellen Sie ein neues Verzeichnis, in dem Sie die komprimierten Dateien für Browser TVSDK herunterladen können.
1. Laden Sie Browser TVSDK von Zendesk herunter, dekomprimieren Sie die Dateien und legen Sie den Ordner &quot;Frameworks&quot;im neuen Verzeichnis ab.
1. Erstellen Sie eine einfache HTML-Vorlage für den Code mit einem `div`.
1. Platzieren Sie diese Vorlage in einer HTML-Datei in dem Verzeichnis, das Sie in Schritt 1 erstellt haben.

   ```
   <!DOCTYPE html> 
   
   <html lang="en"> 
   <head> 
   </head> 
   <body> 
         <div id="videoDiv" width="200" height="200"> 
        <div id="video-controls"></div> 
         </div> 
   </body> 
   </html>
   ```

1. hinzufügen Sie die Browser TVSDK Bibliotheken im Kopfabschnitt.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script>
   ```

1. Fügen Sie für das body-Tag den Abschnitt `onLoad` hinzu.

   ```
   <body onload="startVideo()">
   ```

1. Beginn, der die Funktion `startVideo` implementiert.
1. hinzufügen Sie ein Skript-Tag und erstellen Sie die Funktion `startVideo` im Tag.

   Dies sollte im Kopfabschnitt der Seite sein.

   ```js
   <script> 
    function startVideo(){ 
    } 
   </script>
   ```

1. Erstellen Sie `Adobe.MediaPlayer`.

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Erstellen Sie `MediaPlayerView`.

   >[!TIP]
   >
   >Hier wird das zuvor erstellte `div` verwendet.

   ```js
   var view = new AdobePSDK.MediaPlayerView( 
   document.getElementById("videoDiv")); 
   player.view = view;
   ```

1. hinzufügen Player-Ereignis-Listener.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implementieren Sie den Ereignis-Handler und legen Sie ihn vor den Ereignis-Listener zum Hinzufügen.

   ```js
   var onStatusChange = function (event) { 
    console.log(event.status); 
   
    switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.IDLE: 
      console.log("Player Status: IDLE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZING: 
      console.log("Player Status: INITIALIZING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
      console.log("Player Status: INITIALIZED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARING: 
      console.log("Player Status: PREPARING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
      console.log("Player Status: PREPARED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PLAYING: 
      console.log("Player Status: PLAYING"); 
      //update UI play/pause to show pause icon 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PAUSED: 
      console.log("Player Status: PAUSED"); 
      //update UI play/pause to show play icon & 
      //display pause icon over video 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.SEEKING: 
      console.log("Player Status: SEEKING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.COMPLETE: 
      console.log("Player Status: COMPLETE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: RELEASED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: ERROR"); 
      break; 
    } 
   }; 
   ```

1. Erstellen Sie das `MediaResource`, das den M3U8-Link (oder mpd) übergibt.

   ```js
   var resourceUrl = "https://example.com/a/yourUrl.m3u8"; 
   var resourceType = AdobePSDK.MediaResourceType.HLS; 
   var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, null, false);
   ```

1. Erstellen Sie eine leere Konfiguration und ersetzen Sie die Ressource.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   
   player.replaceCurrentResource(mediaResource, config);
   ```

1. Wenn sich der Player im INITIALIZED-Status befindet, rufen Sie `prepareToPlay` auf.

   ```js
   case INITIALIZED: 
    player.prepareToPlay(); // <- add this line 
    break;
   ```

1. Wenn sich der Player im Status &quot;VORBEREITT&quot;befindet, rufen Sie `play` auf.

   ```js
   case PREPARED: 
    player.play(); 
    break;
   ```

