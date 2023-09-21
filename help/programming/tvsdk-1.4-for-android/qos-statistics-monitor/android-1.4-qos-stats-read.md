---
description: Sie können die Wiedergabe-, Pufferungs- und Gerätestatistiken aus der QOSProvider-Klasse lesen.
title: Lesen von QOS-Wiedergabe, -Pufferung und Gerätestatistiken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Lesen von QOS-Wiedergabe, -Pufferung und Gerätestatistiken{#read-qos-playback-buffering-and-device-statistics}

Sie können die Wiedergabe-, Pufferungs- und Gerätestatistiken aus der QOSProvider-Klasse lesen.

Die `QOSProvider` -Klasse stellt verschiedene Statistiken bereit, darunter Informationen zur Pufferung, Bitraten, Bildraten, Zeitdaten usw.

Es enthält auch Informationen über das Gerät, wie Hersteller, Modell, Betriebssystem, SDK-Version, Geräte-ID des Herstellers und Bildschirmgröße/-dichte.

1. Instanziieren eines Medienplayers
1. Erstellen Sie eine `QOSProvider` -Objekt und fügen Sie es an den Medienplayer an.

   Die `QOSProvider` -Konstruktor verwendet einen Player-Kontext, damit er gerätespezifische Informationen abrufen kann.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistiken.

   Eine Lösung zum Lesen der Wiedergabestatistiken besteht darin, einen Timer zu verwenden, der die neuen QoS-Werte regelmäßig aus der `QOSProvider`. Beispiel:

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
