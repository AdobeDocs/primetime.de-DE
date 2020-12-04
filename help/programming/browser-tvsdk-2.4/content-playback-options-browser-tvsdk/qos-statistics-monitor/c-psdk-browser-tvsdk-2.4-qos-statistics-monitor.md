---
description: Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. Browser TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-description: Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. Browser TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-title: Qualität der Dienstleistungsstatistiken
title: Qualität der Dienstleistungsstatistiken
uuid: e4bb2617-d8a7-4da7-b669-d6ffab2864bb
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---


# Qualität der Dienststatistiken{#quality-of-service-statistics}

Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. Browser TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

## Lesen Sie die QOS-Wiedergabe-, Puffer- und Gerätestatistik {#read-qos-playback-buffering-and-device-statistics}

Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der QOSProvider-Klasse lesen.

Die `QOSProvider`-Klasse stellt verschiedene Statistiken bereit, einschließlich Informationen über Pufferung, Bitraten, Bildraten, Zeitdaten usw.

1. Instanziieren eines Medienplayers.
1. Erstellen Sie ein `QOSProvider`-Objekt und fügen Sie es an den Medienplayer an.

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistik.

   Eine Lösung zum Lesen der Wiedergabestatistik besteht darin, einen Timer zu haben, der die neuen QoS-Werte aus dem `QOSProvider` in regelmäßigen Abständen abruft. Beispiel:

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
