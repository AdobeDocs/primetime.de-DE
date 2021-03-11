---
description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
title: MediaPlayer-Methoden für den Zugriff auf MediaResource-Informationen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# MediaPlayer-Methoden für den Zugriff auf MediaResource-Informationen{#mediaplayer-methods-for-accessing-mediaresource-information}

Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.

<table frame="all" colsep="1" rowsep="1" id="table_77B55D506FE24326A03D97AA087231FF"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> Methode </th> 
   <th colname="3" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Anzeigen-Tags</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;string&gt; ListgetAdTags()  </span> </td> 
   <td colname="3"> <p>Stellt die Liste der Anzeigen-Tags bereit, die für den Anzeigenplatzierungsprozess verwendet werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Live-Stream</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive();  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream live ist; false, wenn es VOD ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM-geschützt</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected();  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream DRM-geschützt ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;drmmetadatainfo&gt; ListgetDRMMetadataInfos();  </span> </td> 
   <td colname="3"> <p>Liste aller DRM-Metadatenobjekte, die im Manifest gefunden werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Untertitel</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions();  </span> </td> 
   <td colname="3"> <p>True, wenn Untertitel-Tracks verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;closedcaptionstrack&gt; ListgetClosedCationsTracks();  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren Untertitelspuren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack();  </span> </td> 
   <td colname="3"> <p>Ruft die aktuelle Untertitelspur ab, die mit <span class="codeph"> SelectClosedCaptionsTrack </span> ausgewählt wurde. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closeCaptionsTrack)  </span> </td> 
   <td colname="3"> <p>Legt eine Untertitelspur als aktuelle Untertitelspur fest. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Alternative Audiospuren</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio();  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream über alternative Audiospuren verfügt. </p> <p>Tipp:  Die Haupt- (Standard-)Audiospur ist ebenfalls Teil der alternativen Liste der Audiospur. </p> <p>TVSDK für Android betrachtet die Hauptaudiospur als eines der Elemente in der alternativen Audiospur-Liste. Aus diesem Grund gibt <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> nur dann false zurück, wenn der Stream überhaupt kein Audio hat. Wenn der Inhalt nur eine Audiospur enthält, gibt diese Methode true zurück und <span class="codeph"> MediaPlayerItem.getAudioTracks </span> gibt eine Liste mit einem einzelnen Element (die Standard-Audiospur) zurück. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;audiotrack&gt; ListgetAudioTracks();  </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;audiotrack&gt; ListgetAudioTracks();  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren alternativen Audiospuren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack();  </span> </td> 
   <td colname="3"> <p>Ruft die mit <span class="codeph"> selectAudioTrack </span> ausgewählte Audiospur ab. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack )  </span> </td> 
   <td colname="3"> <p>Wählt eine Audiospur als aktuelle Audiospur aus. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Zeitgesteuerte Metadaten</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata();  </span> </td> 
   <td colname="3"> <p>True, wenn dem Stream Zeitmetadaten zugeordnet sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;timedmetadata&gt; ListgetTimedMetadata();  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der zeitgesteuerten Metadatenobjekte, die mit dem Stream verknüpft sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic();  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream ein MBR-Stream (multiple bit rate) ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;profile&gt; ListgetProfiles();  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der zugehörigen Profile zur Bitrate. Für jedes Profil können Sie die Bitrate sowie die Höhe und Breite des Profils abrufen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Trick Play</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported();  </span> </td> 
   <td colname="3"> <p>"True", wenn der Player schnelle Vorwärts-, Zurückspulen- und Wiederaufnahme unterstützt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt; Float=""&gt; ListgetAvailablePlaybackRates  </span> </td> 
   <td colname="3"> <p>Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion "Trick-play". </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Medienressource</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource();  </span> </td> 
   <td colname="3"> <p>Gibt die mit diesem Element verknüpfte Medienressource zurück. </p> </td> 
  </tr> 
 </tbody> 
</table>

