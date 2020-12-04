---
description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
seo-description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
seo-title: MediaPlayer-Methoden für den Zugriff auf MediaResource-Informationen
title: MediaPlayer-Methoden für den Zugriff auf MediaResource-Informationen
uuid: c2d18f8e-4107-42bc-a975-9b881aadd27b
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661
workflow-type: tm+mt
source-wordcount: '475'
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
   <td colname="1"> <b>Live-Stream  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isLive():Boolean;  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream live ist; false, wenn es VOD ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM-geschützt</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isProtected():Boolean;  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream DRM-geschützt ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get drmMetadataInfos(): Vektor.&lt;drmmetadatainfo&gt;;  </span> </td> 
   <td colname="3"> <p>Liste aller DRM-Metadatenobjekte, die im Manifest gefunden werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Untertitel</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasClosedCaptions():Boolean;  </span> </td> 
   <td colname="3"> <p>True, wenn Untertitel-Tracks verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get closeCaptionsTracks():Vector.&lt;closedcaptionstrack&gt;;  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren Untertitelspuren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedClosedCaptionsTrack():ClosedCaptionsTrack  </span> </td> 
   <td colname="3"> <p>Ruft die aktuelle Untertitelspur ab, die mit <span class="codeph"> SelectClosedCaptionsTrack </span> ausgewählt wurde. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closeCaptionsTrack: com.adobe.mediacore.info:ClosedCaptionsTrack )  </span> </td> 
   <td colname="3"> <p>Legt eine Untertitelspur als aktuelle Untertitelspur fest. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Alternative Audiospuren  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasAlternateAudio():Boolean;  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream über alternative Audiospuren verfügt. </p> <p>Tipp:  Die Haupt- (Standard-)Audiospur ist ebenfalls Teil der alternativen Liste der Audiospur. </p> <p>TVSDK for Desktop HLS betrachtet die Hauptaudiospur als eines der Elemente in der alternativen Audio-Track-Liste. Aus diesem Grund gibt <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> nur dann false zurück, wenn der Stream überhaupt kein Audio hat. Wenn der Inhalt nur eine Audiospur hat, gibt diese Methode true zurück und <span class="codeph"> get AudioTracks </span> gibt eine Liste mit einem einzelnen Element (die Standard-Audiospur) zurück. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get audioTracks():Vector.&lt;audiotrack&gt;;  </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get audioTracks():Vector.&lt;audiotrack&gt;;  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren alternativen Audiospuren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedAudioTrack():AudioTrack;  </span> </td> 
   <td colname="3"> <p>Ruft die mit <span class="codeph"> selectAudioTrack </span> ausgewählte Audiospur ab. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack: AudioTrack )  </span> </td> 
   <td colname="3"> <p>Wählt eine Audiospur als aktuelle Audiospur aus. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Zeitgesteuerte Metadaten</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasTimedMetadata():Boolean;  </span> </td> 
   <td colname="3"> <p>True, wenn dem Stream Zeitmetadaten zugeordnet sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get timedMetadata():Vector.&lt;timedmetadata&gt;;  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der zeitgesteuerten Metadatenobjekte, die mit dem Stream verknüpft sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isDynamic():Boolean;  </span> </td> 
   <td colname="3"> <p>True, wenn der Stream ein MBR-Stream (multiple bit rate) ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get Profils():Vector.&lt;profile&gt;;  </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der zugehörigen Profile zur Bitrate. Für jedes Profil können Sie die Bitrate sowie die Höhe und Breite des Profils abrufen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Trick Play  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isTrickPlaySupported():Boolean;  </span> </td> 
   <td colname="3"> <p>"True", wenn der Player schnelle Vorwärts-, Zurückspulen- und Wiederaufnahme unterstützt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get availablePlaybackRates():Vector.&lt;number&gt; </span> </td> 
   <td colname="3"> <p>Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion "Trick-play". </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Medienplayer  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get player():MediaPlayer  </span> </td> 
   <td colname="3"> <p>Gibt den Medienplayer zurück, der derzeit mit diesem Player verknüpft ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Medienressource</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get resource():MediaResource;  </span> </td> 
   <td colname="3"> <p>Gibt die mit diesem Element verknüpfte Medienressource zurück. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> function get resourceId():int  </span> </td> 
   <td colname="3"> <p>Gibt die mit diesem Element verknüpfte Medienkennung zurück. </p> </td> 
  </tr> 
 </tbody> 
</table>

