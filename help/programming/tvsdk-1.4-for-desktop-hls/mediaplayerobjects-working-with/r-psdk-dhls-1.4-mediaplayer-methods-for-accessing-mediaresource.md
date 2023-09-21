---
description: Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.
title: MediaPlayer-Methoden für den Zugriff auf MediaResource-Informationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MediaPlayer-Methoden für den Zugriff auf MediaResource-Informationen{#mediaplayer-methods-for-accessing-mediaresource-information}

Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.

<table frame="all" colsep="1" rowsep="1" id="table_77B55D506FE24326A03D97AA087231FF"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> Methode </th> 
   <th colname="3" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Live-Stream </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isLive():Boolean; </span> </td> 
   <td colname="3"> <p>True , wenn der Stream live ist, false , wenn es VOD ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM-geschützt</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get isProtected():Boolean; </span> </td> 
   <td colname="3"> <p>True , wenn der Stream DRM-geschützt ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get drmMetadataInfos(): Vector.&lt;drmmetadatainfo&gt;; </span> </td> 
   <td colname="3"> <p>Listet alle DRM-Metadatenobjekte auf, die im Manifest gefunden wurden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Geschlossene Untertitel</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasClosedCaptions():Boolean; </span> </td> 
   <td colname="3"> <p>True , wenn geschlossene Untertitelspuren verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get closedCaptionsTracks():Vector.&lt;closedcaptionstrack&gt;; </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren Tracks mit geschlossenen Untertiteln. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get selectedClosedCaptionsTrack():ClosedCaptionsTrack </span> </td> 
   <td colname="3"> <p>Ruft die aktuelle Untertitelspur ab, die mit <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closedCaptionsTrack: com.adobe.mediacore.info:ClosedCaptionsTrack ) </span> </td> 
   <td colname="3"> <p>Legt fest, dass eine Untertitelspur die aktuelle Untertitelspur ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Alternative Audiospuren </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasAlternateAudio():Boolean; </span> </td> 
   <td colname="3"> <p>True , wenn der Stream alternative Audiospuren hat. </p> <p>Tipp: Der Haupt-Audio-Track (Standard) ist ebenfalls Teil der alternativen Audio-Track-Liste. </p> <p>TVSDK für Desktop HLS betrachtet den Haupt-Audio-Track als eines der Elemente in der alternativen Audio-Track-Liste. Aus diesem Grund ist der einzige Fall, in dem <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> gibt "false"zurück, wenn der Stream überhaupt keine Audiowiedergabe hat. Wenn der Inhalt nur eine Audiospur enthält, gibt diese Methode "true"zurück und <span class="codeph"> get AudioTracks </span> gibt eine Liste mit einem einzelnen Element (dem standardmäßigen Audio-Track) zurück. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get audioTracks():Vector.&lt;audiotrack&gt;; </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get audioTracks():Vector.&lt;audiotrack&gt;; </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren alternativen Audiospuren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get selectedAudioTrack():AudioTrack; </span> </td> 
   <td colname="3"> <p>Ruft den mit ausgewählten Audio-Track ab <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack: AudioTrack ) </span> </td> 
   <td colname="3"> <p>Wählt einen Audio-Track als aktuellen Audio-Track aus. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Zeitgesteuerte Metadaten</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasTimedMetadata():Boolean; </span> </td> 
   <td colname="3"> <p>True , wenn dem Stream zeitgesteuerte Metadaten zugeordnet sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get timedMetadata():Vector.&lt;timedmetadata&gt;; </span> </td> 
   <td colname="3"> <p>Stellt eine Liste der zeitgesteuerten Metadatenobjekte bereit, die mit dem Stream verknüpft sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isDynamic():Boolean; </span> </td> 
   <td colname="3"> <p>True , wenn es sich bei dem Stream um einen MBR-Stream (multiple bit rate) handelt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get profiles():Vector.&lt;profile&gt;; </span> </td> 
   <td colname="3"> <p>Enthält eine Liste der zugehörigen Bitratenprofile. Für jedes Profil können Sie dessen Bitrate sowie Höhe und Breite abrufen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Trick play </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isTrickPlaySupported():Boolean; </span> </td> 
   <td colname="3"> <p>True , wenn der Player die schnelle Weiterleitung, Zurückspulen und Wiederaufnehmen unterstützt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get availablePlaybackRates():Vector.&lt;Number&gt; </span> </td> 
   <td colname="3"> <p>Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion "Trick-Play". </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Medienplayer </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get player():MediaPlayer </span> </td> 
   <td colname="3"> <p>Gibt den Medienplayer zurück, der diesem Player derzeit zugeordnet ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Medienressource</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Funktion get resource():MediaResource; </span> </td> 
   <td colname="3"> <p>Gibt die diesem Element zugeordnete Medienressource zurück. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> function get resourceId():int </span> </td> 
   <td colname="3"> <p>Gibt die mit diesem Element verknüpfte Medienkennung zurück. </p> </td> 
  </tr> 
 </tbody> 
</table>
