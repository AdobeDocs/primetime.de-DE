---
description: Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
title: Qualitätsstatistiken der Dienstleistung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Qualitätsstatistiken der Dienstleistung {#quality-of-service-statistics}

Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

TVSDK bietet außerdem Informationen zu den folgenden heruntergeladenen Ressourcen:

* Wiedergabelisten-/Manifestdateien
* Dateifragmente
* Tracking-Informationen für Dateien

## Auf Fragmentebene mithilfe von Ladeinformationen verfolgen {#section_4439D91E8EDC45588EF1D7BE25697350}

Sie können Informationen zur Servicequalität (QoS) über heruntergeladene Ressourcen, wie Fragmente und Tracks, aus dem `LoadInformation` -Klasse.

1. Implementieren und registrieren Sie die `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` Ereignis-Listener.
1. Aufruf `event.getLoadInformation()` zum Lesen der relevanten Daten aus der `event` -Parameter, der an den Rückruf übergeben wird.

   >[!NOTE]
   >
   >Weitere Informationen `LoadInformation`, siehe [3.0 für Android (Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.0/index.html) API-Dokumente.

## Lesen von QOS-Wiedergabe, -Pufferung und Gerätestatistiken {#section_D21722600F324E67A9F06234D338B243}

Sie können die Wiedergabe-, Pufferungs- und Gerätestatistiken aus dem `QOSProvider` -Klasse.

Die `QOSProvider` -Klasse stellt verschiedene Statistiken bereit, darunter Informationen zur Pufferung, Bitraten, Bildraten, Zeitdaten usw. Es enthält auch Informationen über das Gerät, wie Hersteller, Modell, Betriebssystem, SDK-Version, Geräte-ID des Herstellers und Bildschirmgröße/-dichte.

1. Instanziieren eines Medienplayers
1. Erstellen Sie eine `QOSProvider` -Objekt und fügen Sie es an den Medienplayer an.

   Die `QOSProvider` -Konstruktor verwendet einen Player-Kontext, damit er gerätespezifische Informationen abrufen kann.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistiken.

   Eine Lösung zum Lesen der Wiedergabestatistiken besteht darin, einen Timer zu verwenden, der die neuen QoS-Werte regelmäßig aus der `QOSProvider`.

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
