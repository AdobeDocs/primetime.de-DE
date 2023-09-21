---
description: Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
title: Qualitätsstatistiken der Dienstleistung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Qualitätsstatistiken der Dienstleistung {#quality-of-service-statistics}

Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

TVSDK bietet außerdem Informationen zu den folgenden heruntergeladenen Ressourcen:

* Wiedergabelisten-/Manifestdateien
* Dateifragmente
* Tracking-Informationen für Dateien

## Auf Fragmentebene mithilfe von Ladeinformationen verfolgen {#track-at-the-fragment-level-using-load-information}

Sie können Informationen zur Servicequalität (QoS) zu heruntergeladenen Ressourcen, z. B. Fragmenten und Tracks, aus der LoadInformation-Klasse lesen.

1. Implementieren des `onLoadInformationAvailable` Callback-Ereignis-Listener.

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. Registrieren Sie den Ereignis-Listener, den TVSDK jedes Mal aufruft, wenn ein Fragment heruntergeladen wurde.

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. Lesen Sie die interessanten Daten aus der `LoadInformation` wird an den Rückruf übergeben.

   <table id="table_75E61A2EB25E435DB631166A7FF64757"> 
   <thead> 
   <tr> 
      <th colname="col01" class="entry"> Eigenschaft </th> 
      <th colname="col1" class="entry"> Typ </th> 
      <th colname="col2" class="entry"> Beschreibung </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col01"> <span class="codeph"> downloadDauer </span> </td> 
      <td colname="col1"> <p>Zahl </p> </td> 
      <td colname="col2"> <p>Die Dauer des Downloads in Millisekunden. </p> <p>TVSDK unterscheidet nicht zwischen der Zeit, die der Client für die Verbindung mit dem Server benötigt hat, und der Zeit, die zum Herunterladen des vollständigen Fragments erforderlich war. Wenn das Herunterladen eines 10-MB-Segments beispielsweise 8 Sekunden dauert, stellt TVSDK diese Informationen bereit, teilt Ihnen jedoch nicht mit, dass der Download des gesamten Fragments 4 Sekunden bis zum ersten Byte und weitere 4 Sekunden dauerte. </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <p>Zahl </p> </td> 
      <td colname="col2"> Die Mediendauer der heruntergeladenen Fragmente in Millisekunden. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> size </span> </td> 
      <td colname="col1"> <p>Zahl </p> </td> 
      <td colname="col2"> Die Größe der heruntergeladenen Ressource in Byte. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> Der Index der entsprechenden Spur, sofern bekannt; andernfalls 0. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Der Name des entsprechenden Tracks, sofern bekannt; andernfalls null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Der Typ des entsprechenden Tracks, sofern bekannt; andernfalls null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Was TVSDK heruntergeladen hat. Eine der folgenden Optionen: 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST - Eine Wiedergabeliste/ein Manifest </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">FRAGMENT - Ein Fragment </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK - Ein Fragment, das mit einem bestimmten Track verknüpft ist </li> 
      </ul> Manchmal ist es möglicherweise nicht möglich, den Ressourcentyp zu erkennen. Tritt dies ein, wird die DATEI zurückgegeben. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Die URL, die auf die heruntergeladene Ressource verweist. </td> 
   </tr> 
   </tbody> 
   </table>

## Lesen von QOS-Wiedergabe, -Pufferung und Gerätestatistiken {#read-qos-playback-buffering-and-device-statistics}

Sie können die Wiedergabe-, Pufferungs- und Gerätestatistiken aus der QOSProvider-Klasse lesen.

Die `QOSProvider` -Klasse stellt verschiedene Statistiken bereit, darunter Informationen zur Pufferung, Bitraten, Bildraten, Zeitdaten usw.

Es enthält auch Informationen über das Gerät, wie Hersteller, Modell, Betriebssystem, SDK-Version und Bildschirmgröße/-dichte.

1. Instanziieren eines Medienplayers
1. Erstellen Sie eine `QOSProvider` -Objekt und fügen Sie es an den Medienplayer an.

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optional) Lesen Sie die Wiedergabestatistiken.

   Eine Lösung zum Lesen der Wiedergabestatistiken besteht darin, einen Timer zu verwenden, der die neuen QoS-Werte regelmäßig aus der `QOSProvider`. Beispiel:

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
