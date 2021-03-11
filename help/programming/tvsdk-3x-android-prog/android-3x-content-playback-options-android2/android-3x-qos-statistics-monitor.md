---
description: Die Servicequalität (Quality of Service, QoS) bietet eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
title: Qualität der Dienstleistungsstatistiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Qualität der Dienststatistiken {#quality-of-service-statistics}

Die Servicequalität (Quality of Service, QoS) bietet eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

TVSDK bietet außerdem Informationen zu den folgenden heruntergeladenen Ressourcen:

* Playlist-/Manifestdateien
* Dateifragmente
* Dateiverfolgung

## Verfolgen auf Fragmentebene mithilfe der Ladeinformationen {#section_4439D91E8EDC45588EF1D7BE25697350}

Sie können Servicequalitätsinformationen (QoS) zu heruntergeladenen Ressourcen wie Fragmenten und Spuren von der `LoadInformation`-Klasse lesen.

1. Implementieren und registrieren Sie den `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE`-Ereignis-Listener.
1. Rufen Sie `event.getLoadInformation()` auf, um die relevanten Daten aus dem Parameter `event` zu lesen, der an den Rückruf weitergeleitet wird.

   >[!NOTE]
   >
   >Weitere Informationen zu `LoadInformation` finden Sie unter [3.0 für Android (Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.0/index.html)-API-Dokumente.

## Lesen Sie die QOS-Wiedergabe-, Puffer- und Gerätestatistik {#section_D21722600F324E67A9F06234D338B243}

Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der `QOSProvider`-Klasse lesen.

Die `QOSProvider`-Klasse stellt verschiedene Statistiken bereit, einschließlich Informationen über Pufferung, Bitraten, Bildraten, Zeitdaten usw. Es enthält außerdem Informationen zum Gerät, wie Hersteller, Modell, Betriebssystem, SDK-Version, Geräte-ID des Herstellers und Bildschirmgröße/Dichte.

1. Instanziieren eines Medienplayers.
1. Erstellen Sie ein `QOSProvider`-Objekt und fügen Sie es an den Medienplayer an.

   Der Konstruktor `QOSProvider` nimmt einen Player-Kontext, damit er gerätespezifische Informationen abrufen kann.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistik.

   Eine Lösung zum Lesen der Wiedergabestatistik besteht darin, einen Timer zu haben, der die neuen QoS-Werte aus dem `QOSProvider` in regelmäßigen Abständen abruft.

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
