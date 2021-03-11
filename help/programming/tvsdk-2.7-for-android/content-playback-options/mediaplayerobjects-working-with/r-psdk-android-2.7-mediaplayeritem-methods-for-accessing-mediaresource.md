---
description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
title: MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.

<table frame="all" colsep="1" rowsep="1" id="table_F6006A9167044AC087A6ECB20B8CCD5D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> Methode </th> 
   <th colname="3" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Anzeigen-Tags</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;string&gt; ListgetAdTags()  </span> </td> 
   <td colname="3"> Stellt die Liste der Anzeigen-Tags bereit, die für den Anzeigenplatzierungsprozess verwendet werden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Live-Stream</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive();  </span> </td> 
   <td colname="3"> True, wenn der Stream live ist; false, wenn es VOD ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM-geschützt</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected();  </span> </td> 
   <td colname="3"> True, wenn der Stream DRM-geschützt ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;drmmetadatainfo&gt; ListgetDRMMetadataInfos();  </span> </td> 
   <td colname="3"> Liste aller DRM-Metadatenobjekte, die im Manifest gefunden werden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Untertitel</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions();  </span> </td> 
   <td colname="3"> True, wenn Untertitel-Tracks verfügbar sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;closedcaptionstrack&gt; ListgetClosedCationsTracks();  </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren Untertitelspuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack();  </span> </td> 
   <td colname="3"> Ruft die aktuelle Untertitelspur ab, die mit <span class="codeph"> SelectClosedCaptionsTrack </span> ausgewählt wurde. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closeCaptionsTrack)  </span> </td> 
   <td colname="3"> Legt eine Untertitelspur als aktuelle Untertitelspur fest. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Alternative Audiospuren</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio();  </span> </td> 
   <td colname="3"> True, wenn der Stream über alternative Audiospuren verfügt. <p>Hinweis:  Die Haupt- (Standard-)Audiospur ist ebenfalls Teil der alternativen Liste der Audiospur. </p> <p>TVSDK für Android betrachtet die Hauptaudiospur als eines der Elemente in der alternativen Audiospur-Liste. Aus diesem Grund gibt <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> nur dann false zurück, wenn der Stream überhaupt kein Audio hat. Wenn der Inhalt nur eine Audiospur enthält, gibt diese Methode true zurück und <span class="codeph"> MediaPlayerItem.getAudioTracks </span> gibt eine Liste mit einem einzelnen Element (die Standard-Audiospur) zurück. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;audiotrack&gt; ListgetAudioTracks();  </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack();  </span> </td> 
   <td colname="3"> Ruft die mit <span class="codeph"> selectAudioTrack </span> ausgewählte Audiospur ab. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack )  </span> </td> 
   <td colname="3"> Wählt eine Audiospur als aktuelle Audiospur aus. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Zeitgesteuerte Metadaten</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata();  </span> </td> 
   <td colname="3"> True, wenn dem Stream Zeitmetadaten zugeordnet sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;timedmetadata&gt; ListgetTimedMetadata();  </span> </td> 
   <td colname="3"> Bietet eine Liste der zeitgesteuerten Metadatenobjekte, die mit dem Stream verknüpft sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Mehrere Profil (Bitraten)</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic();  </span> </td> 
   <td colname="3"> True, wenn der Stream ein MBR-Stream (multiple bit rate) ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;profile&gt; ListgetProfiles();  </span> </td> 
   <td colname="3"> Bietet eine Liste der zugehörigen Profile zur Bitrate. Für jedes Profil können Sie die Bitrate sowie die Höhe und Breite des Profils abrufen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Profil getSelectedProfile()  </span> </td> 
   <td colname="3"> Ruft das aktuell ausgewählte Profil ab. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Trick Play</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported();  </span> </td> 
   <td colname="3"> "True", wenn der Player schnelle Vorwärts-, Zurückspulen- und Wiederaufnahme unterstützt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt; Float=""&gt; ListgetAvailablePlaybackRates()  </span> </td> 
   <td colname="3"> Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion "Trick-play". </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate()  </span> </td> 
   <td colname="3"> Ruft die derzeit ausgewählte Wiedergabegeschwindigkeit ab. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig()  </span> </td> 
   <td colname="3"> Gibt die mit diesem Element verknüpfte Instanz <span class="codeph"> MediaPlayerItemConfig </span> zurück. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Medienressource</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource();  </span> </td> 
   <td colname="3"> Gibt die mit diesem Element verknüpfte Medienressource zurück. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId()  </span> </td> 
   <td colname="3"> Gibt die mit diesem Element verknüpfte Medienkennung zurück. Diese ID wird festgelegt, wenn das Element mit <span class="codeph"> MediaPlayerItemLoader.load </span> geladen wird. </td> 
  </tr> 
 </tbody> 
</table>
