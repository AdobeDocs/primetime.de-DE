---
description: Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der QOSProvider-Klasse lesen.
seo-description: Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der QOSProvider-Klasse lesen.
seo-title: Lesen der QOS-Wiedergabe, -Pufferung und Gerätestatistik
title: Lesen der QOS-Wiedergabe, -Pufferung und Gerätestatistik
uuid: 5ee631fc-cd6f-4f35-8621-2ffdc51a57c7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Lesen der QOS-Wiedergabe, -Pufferung und Gerätestatistik{#read-qos-playback-buffering-and-device-statistics}

Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der QOSProvider-Klasse lesen.

Die `QOSProvider` Klasse stellt verschiedene Statistiken bereit, darunter Informationen über Pufferung, Bitraten, Bildraten, Zeitdaten usw.

Es enthält außerdem Informationen zum Gerät, wie Hersteller, Modell, Betriebssystem, SDK-Version und Bildschirmgröße/-dichte.

1. Instanziieren eines Medienplayers.
1. Erstellen Sie ein `QOSProvider` Objekt und fügen Sie es an den Medienplayer an.

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistik.

   Eine Lösung zum Lesen der Wiedergabestatistik besteht darin, einen Timer zu haben, der die neuen QoS-Werte in regelmäßigen Abständen von der `QOSProvider`abruft. Beispiel:

   ```
   var qosTimer:Timer = new Timer(1000); // every 1 second  
   qosTimer.addEventListener(TimerEvent.Timer, onQoSTimer);  
   qosTimer.start(); 
   private function onQoSTimer(event:TimerEvent):void { 
       var playbackInformation:PlaybackInformation = _mediaQosProvider.getPlaybackInformation(); 
       qosInfo["Frame rate"] = playbackInformation.frameRate.toFixed();  
       qosInfo["Dropped frames"] = playbackInformation.droppedFrameCount.toFixed(); 
       qosInfo["Bitrate"] = playbackInformation.bitrate.toFixed(); 
       qosInfo["Bandwidth"] = playbackInformation.perceivedBandwidth; 
       qosInfo["Buffering time"] = playbackInformation.bufferingTime.toFixed(); 
       qosInfo["Buffer length"] = playbackInformation.bufferLength.toFixed();  
       qosInfo["Buffer time"] = playbackInformation.bufferTime.toFixed(); 
       qosInfo["Empty buffer count"] = playbackInformation.emptyBufferCount.toFixed();  
       qosInfo["Time to load"] = playbackInformation.timeToLoad.toFixed();  
       qosInfo["Time to start"] = playbackInformation.timeToStart.toFixed(); 
       qosView.update(qosInfo); 
   }
   ```

1. (Optional) Lesen Sie die gerätespezifischen Informationen.

   ```
   // Show device information 
   var deviceInfo:DeviceInformation = new QOSProvider.deviceInformation; 
   qosInfo["deviceModel"] = deviceInfo.manufacturer +"-" + deviceInfo.model; 
   qosInfo["os"] = deviceInfo.os;  
   qosInfo["runtime"] = deviceInfo.runtimeVersion;  
   qosInfo["widthPixels"] = deviceInfo.widthPixels;  
   qosInfo["heightPixels"] = deviceInfo.heightPixels; 
   qosView.update(qosInfo); 
   ```

