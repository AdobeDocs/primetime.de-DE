---
description: Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der QOSProvider-Klasse lesen.
seo-description: Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der QOSProvider-Klasse lesen.
seo-title: Lesen der QOS-Wiedergabe, -Pufferung und Gerätestatistik
title: Lesen der QOS-Wiedergabe, -Pufferung und Gerätestatistik
uuid: 19228a50-3721-4dc1-89b6-97458518e272
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 1%

---


# Lesen Sie die QOS-Wiedergabe-, Puffer- und Gerätestatistiken{#read-qos-playback-buffering-and-device-statistics}

Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der QOSProvider-Klasse lesen.

Die `QOSProvider`-Klasse stellt verschiedene Statistiken bereit, einschließlich Informationen über Pufferung, Bitraten, Bildraten, Zeitdaten usw.

Es enthält außerdem Informationen zum Gerät, wie Hersteller, Modell, Betriebssystem, SDK-Version, Geräte-ID des Herstellers und Bildschirmgröße/Dichte.

1. Instanziieren eines Medienplayers.
1. Erstellen Sie ein `QOSProvider`-Objekt und fügen Sie es an den Medienplayer an.

   Der Konstruktor `QOSProvider` nimmt einen Player-Kontext, damit er gerätespezifische Informationen abrufen kann.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistik.

   Eine Lösung zum Lesen der Wiedergabestatistik besteht darin, einen Timer zu haben, der die neuen QoS-Werte aus dem `QOSProvider` in regelmäßigen Abständen abruft. Beispiel:

   ```java
   _playbackClock = new Clock(PLAYBACK_CLOCK, 1000); // every 1 second 
   
   _playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           getActivity().runOnUiThread(new Runnable() { 
               @Override 
               public void run() { 
                   PlaybackInformation playbackInformation = _mediaQosProvider.getPlaybackInformation();  
                   setQosItem("Frame rate", (int) playbackInformation.getFrameRate());  
                   setQosItem("Dropped frames", (int) playbackInformation.getDroppedFrameCount()); 
                   setQosItem("Bitrate", (int) playbackInformation.getBitrate()); 
                   setQosItem("Buffering time", (int) playbackInformation.getBufferingTime());  
                   setQosItem("Buffer length", (int) playbackInformation.getBufferLength());  
                   setQosItem("Buffer time", (int) playbackInformation.getBufferTime());  
                   setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount());  
                   setQosItem("Time to load", (int) playbackInformation.getTimeToLoad());  
                   setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); 
                   setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); 
                   setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());   
                   playbackInformation.getPerceivedBandwidth()); 
               } 
           }); 
       }; 
   }; 
   ```

1. (Optional) Lesen Sie die gerätespezifischen Informationen.

   ```java
   // Show device information 
   DeviceInformation deviceInfo =  
     new QOSProvider(parent.getApplicationContext()).getDeviceInformation(); 
   tv = (TextView) view.findViewById(R.id.aboutDeviceModel); 
   tv.setText(parent.getString(R.string.aboutDeviceModel) + " " +  
     deviceInfo.getManufacturer() + " - " + deviceInfo.getModel()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceSoftware); 
   tv.setText(parent.getString(R.string.aboutDeviceSoftware) + " " +  
     deviceInfo.getOS() + ", SDK: " + deviceInfo.getSDK()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceResolutin); 
   String orientation = parent.getResources().getConfiguration().orientation ==  
     Configuration.ORIENTATION_LANDSCAPE ? "landscape" : "portrait"; 
   tv.setText(parent.getString(R.string.aboutDeviceResolution) + " " +  
     deviceInfo.getWidthPixels() + "x" + deviceInfo.getHeightPixels() +  
     " (" + orientation + ")"); 
   ```

