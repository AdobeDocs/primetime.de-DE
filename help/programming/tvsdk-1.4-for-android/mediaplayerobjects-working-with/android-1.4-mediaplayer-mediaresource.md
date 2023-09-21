---
description: Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.
title: MediaPlayer-Methoden für den Zugriff auf MediaResource-Informationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '405'
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
   <td colname="1"> <b>Anzeigen-Tags</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;string&gt; getAdTags() </span> </td> 
   <td colname="3"> <p>Stellt die Liste der Anzeigen-Tags bereit, die für den Anzeigenplatzierungsprozess verwendet werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Live-Stream</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive(); </span> </td> 
   <td colname="3"> <p>True , wenn der Stream live ist, false , wenn es VOD ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM-geschützt</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected(); </span> </td> 
   <td colname="3"> <p>True , wenn der Stream DRM-geschützt ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;drmmetadatainfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> <p>Listet alle DRM-Metadatenobjekte auf, die im Manifest gefunden wurden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Geschlossene Untertitel</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions(); </span> </td> 
   <td colname="3"> <p>True , wenn geschlossene Untertitelspuren verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;closedcaptionstrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren Tracks mit geschlossenen Untertiteln. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> <p>Ruft die aktuelle Untertitelspur ab, die mit <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) </span> </td> 
   <td colname="3"> <p>Legt fest, dass eine Untertitelspur die aktuelle Untertitelspur ist. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Alternative Audiospuren</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio(); </span> </td> 
   <td colname="3"> <p>True , wenn der Stream alternative Audiospuren hat. </p> <p>Tipp: Der Haupt-Audio-Track (Standard) ist ebenfalls Teil der alternativen Audio-Track-Liste. </p> <p>TVSDK für Android betrachtet den Haupt-Audio-Track als eines der Elemente in der alternativen Audio-Track-Liste. Aus diesem Grund ist der einzige Fall, in dem <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> gibt "false"zurück, wenn der Stream überhaupt keine Audiowiedergabe hat. Wenn der Inhalt nur eine Audiospur enthält, gibt diese Methode "true"zurück und <span class="codeph"> MediaPlayerItem.getAudioTracks </span> gibt eine Liste mit einem einzelnen Element (dem standardmäßigen Audio-Track) zurück. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;audiotrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;audiotrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> <p>Bietet eine Liste der verfügbaren alternativen Audiospuren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> <p>Ruft den mit ausgewählten Audio-Track ab <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> <p>Wählt einen Audio-Track als aktuellen Audio-Track aus. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Zeitgesteuerte Metadaten</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata(); </span> </td> 
   <td colname="3"> <p>True , wenn dem Stream zeitgesteuerte Metadaten zugeordnet sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;timedmetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> <p>Stellt eine Liste der zeitgesteuerten Metadatenobjekte bereit, die mit dem Stream verknüpft sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic(); </span> </td> 
   <td colname="3"> <p>True , wenn es sich bei dem Stream um einen MBR-Stream (multiple bit rate) handelt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;profile&gt; getProfiles(); </span> </td> 
   <td colname="3"> <p>Enthält eine Liste der zugehörigen Bitratenprofile. Für jedes Profil können Sie dessen Bitrate sowie Höhe und Breite abrufen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Trick play</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported(); </span> </td> 
   <td colname="3"> <p>True , wenn der Player die schnelle Weiterleitung, Zurückspulen und Wiederaufnehmen unterstützt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt; Float&gt; getAvailablePlaybackRates </span> </td> 
   <td colname="3"> <p>Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion "Trick-Play". </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Medienressource</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> <p>Gibt die diesem Element zugeordnete Medienressource zurück. </p> </td> 
  </tr> 
 </tbody> 
</table>
