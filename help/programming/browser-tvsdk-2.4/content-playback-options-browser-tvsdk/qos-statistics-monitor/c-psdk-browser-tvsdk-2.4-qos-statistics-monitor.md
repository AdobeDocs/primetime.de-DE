---
description: Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. Browser TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
title: Qualitätsstatistiken der Dienstleistung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Qualitätsstatistiken der Dienstleistung{#quality-of-service-statistics}

Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. Browser TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

## Lesen von QOS-Wiedergabe, -Pufferung und Gerätestatistiken {#read-qos-playback-buffering-and-device-statistics}

Sie können die Wiedergabe-, Pufferungs- und Gerätestatistiken aus der QOSProvider-Klasse lesen.

Die `QOSProvider` -Klasse stellt verschiedene Statistiken bereit, darunter Informationen zur Pufferung, Bitraten, Bildraten, Zeitdaten usw.

1. Instanziieren eines Medienplayers
1. Erstellen Sie eine `QOSProvider` -Objekt und fügen Sie es an den Medienplayer an.

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistiken.

   Eine Lösung zum Lesen der Wiedergabestatistiken besteht darin, einen Timer zu verwenden, der die neuen QoS-Werte regelmäßig aus der `QOSProvider`. Beispiel:

   ```js
   var qosTimer = (function () { 
       var ref = null, 
       qosChangeInterval = 500, // in milliseconds 
   
       startTimer = function () { 
           var playbackInformation = qosProvider.playbackInformation; 
        console.log("Frame rate", playbackInformation.frameRate); 
           console.log ("Dropped frames", playbackInformation.droppedFrameCount); 
           console.log ("Bitrate", playbackInformation.bitrate); 
           console.log ("Buffering time", playbackInformation.bufferingTime); 
           console.log ("Buffer length", playbackInformation.bufferLength); 
           console.log ("Buffer time", playbackInformation.bufferTime); 
           console.log ("Empty buffer count", playbackInformation.emptyBufferCount); 
           console.log ("Time to load", playbackInformation.timeToLoad); 
           console.log ("Time to start", playbackInformation.timeToStart); 
           ref = window.setTimeout(startTimer, qosChangeInterval); 
       }; 
   
       return { 
           start: function () { 
               if (ref !== null) { 
                   // don't start another timeout if one already exists. 
                   return; 
               } 
               startTimer(); 
           }, 
   
           stop: function () { 
               window.clearTimeout(ref); 
               ref = null; 
           } 
       };  
   })() 
   
   qosTimer.start(); 
   ```

1. (Optional) Lesen Sie die gerätespezifischen Informationen.

   ```js
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider().deviceInformation; 
   console.log("OS: "+ deviceInfo.getOS()); 
   console.log("Width: "+ deviceInfo.getWidthPixels() +  
               "Height: "+ deviceInfo.getHeightPixels() );
   ```
