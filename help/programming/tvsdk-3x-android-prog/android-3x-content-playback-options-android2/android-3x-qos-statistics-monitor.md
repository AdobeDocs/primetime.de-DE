---
description: Die Servicequalität (Quality of Service, QoS) bietet eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-description: Die Servicequalität (Quality of Service, QoS) bietet eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-title: Qualität der Dienstleistungsstatistiken
title: Qualität der Dienstleistungsstatistiken
uuid: 3d66ed44-9d4a-4162-962f-e238575ff2dd
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Qualität der Dienstleistungsstatistiken {#quality-of-service-statistics}

Die Servicequalität (Quality of Service, QoS) bietet eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

TVSDK bietet außerdem Informationen zu den folgenden heruntergeladenen Ressourcen:

* Playlist-/Manifestdateien
* Dateifragmente
* Dateiverfolgung

## Verfolgen auf Fragmentebene mithilfe der Ladeinformationen {#section_4439D91E8EDC45588EF1D7BE25697350}

Sie können Servicequalitätsinformationen (QoS) zu heruntergeladenen Ressourcen wie Fragmenten und Tracks aus der `LoadInformation` Klasse lesen.

1. Implementieren und registrieren Sie den `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` Ereignis-Listener.
1. Aufruf `event.getLoadInformation()` zum Lesen der relevanten Daten aus dem `event` Parameter, der an den Rückruf übergeben wird.

   >[!NOTE]
   >
   >Weitere Informationen `LoadInformation`finden Sie unter [3.0 für Android-(Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.0/index.html) API-Dokumente.

## Lesen der QOS-Wiedergabe, -Pufferung und Gerätestatistik {#section_D21722600F324E67A9F06234D338B243}

Sie können die Statistiken zur Wiedergabe, Pufferung und zum Gerät aus der `QOSProvider` Klasse lesen.

Die `QOSProvider` Klasse stellt verschiedene Statistiken bereit, darunter Informationen über Pufferung, Bitraten, Bildraten, Zeitdaten usw. Es enthält außerdem Informationen zum Gerät, wie Hersteller, Modell, Betriebssystem, SDK-Version, Geräte-ID des Herstellers und Bildschirmgröße/Dichte.

1. Instanziieren eines Medienplayers.
1. Erstellen Sie ein `QOSProvider` Objekt und fügen Sie es an den Medienplayer an.

   Der `QOSProvider` Konstruktor verwendet einen Player-Kontext, um gerätespezifische Informationen abrufen zu können.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistik.

   Eine Lösung zum Lesen der Wiedergabestatistik besteht darin, einen Timer zu haben, der die neuen QoS-Werte in regelmäßigen Abständen von der `QOSProvider`abruft.

   Beispiel:

   ```java
   _playbackClock = new Clock(PLAYBACK_CLOCK, 1000); // every 1 second 
   _playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           getActivity().runOnUiThread(new Runnable() { 
               @Override 
               public void run() { 
                   PlaybackInformation playbackInformation =  
                     _mediaQosProvider.getPlaybackInformation();  
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
   DeviceInformation deviceInfo = new QOSProvider(parent.getApplicationContext()). 
                                  getDeviceInformation(); 
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
