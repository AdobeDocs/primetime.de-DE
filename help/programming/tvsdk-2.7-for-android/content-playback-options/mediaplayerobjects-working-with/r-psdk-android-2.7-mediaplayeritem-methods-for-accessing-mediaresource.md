---
description: Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.
title: MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.

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
   <td colname="2"> <span class="codeph"> Liste&lt;string&gt; getAdTags() </span> </td> 
   <td colname="3"> Stellt die Liste der Anzeigen-Tags bereit, die für den Anzeigenplatzierungsprozess verwendet werden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Live-Stream</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive(); </span> </td> 
   <td colname="3"> True , wenn der Stream live ist, false , wenn es VOD ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM-geschützt</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected(); </span> </td> 
   <td colname="3"> True , wenn der Stream DRM-geschützt ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;drmmetadatainfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> Listet alle DRM-Metadatenobjekte auf, die im Manifest gefunden wurden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Geschlossene Untertitel</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions(); </span> </td> 
   <td colname="3"> True , wenn geschlossene Untertitelspuren verfügbar sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;closedcaptionstrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren Tracks mit geschlossenen Untertiteln. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> Ruft die aktuelle Untertitelspur ab, die mit <span class="codeph"> SelectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) </span> </td> 
   <td colname="3"> Legt fest, dass eine Untertitelspur die aktuelle Untertitelspur ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Alternative Audiospuren</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio(); </span> </td> 
   <td colname="3"> True , wenn der Stream alternative Audiospuren hat. <p>Hinweis: Der Haupt-Audio-Track (Standard) ist ebenfalls Teil der alternativen Audio-Track-Liste. </p> <p>TVSDK für Android betrachtet den Haupt-Audio-Track als eines der Elemente in der alternativen Audio-Track-Liste. Aus diesem Grund ist der einzige Fall, in dem <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> gibt "false"zurück, wenn der Stream überhaupt keine Audiowiedergabe hat. Wenn der Inhalt nur eine Audiospur enthält, gibt diese Methode "true"zurück und <span class="codeph"> MediaPlayerItem.getAudioTracks </span> gibt eine Liste mit einem einzelnen Element (dem standardmäßigen Audio-Track) zurück. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;audiotrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> Ruft den mit ausgewählten Audio-Track ab <span class="codeph"> selectAudioTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> Wählt einen Audio-Track als aktuellen Audio-Track aus. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Zeitgesteuerte Metadaten</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata(); </span> </td> 
   <td colname="3"> True , wenn dem Stream zeitgesteuerte Metadaten zugeordnet sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;timedmetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> Stellt eine Liste der zeitgesteuerten Metadatenobjekte bereit, die mit dem Stream verknüpft sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Mehrere Profile (Bitraten)</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic(); </span> </td> 
   <td colname="3"> True , wenn es sich bei dem Stream um einen MBR-Stream (multiple bit rate) handelt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;profile&gt; getProfiles(); </span> </td> 
   <td colname="3"> Enthält eine Liste der zugehörigen Bitratenprofile. Für jedes Profil können Sie dessen Bitrate sowie Höhe und Breite abrufen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Profil getSelectedProfile() </span> </td> 
   <td colname="3"> Ruft das aktuell ausgewählte Profil ab. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Trick play</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported(); </span> </td> 
   <td colname="3"> True , wenn der Player die schnelle Weiterleitung, Zurückspulen und Wiederaufnehmen unterstützt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt; Float&gt; getAvailablePlaybackRates() </span> </td> 
   <td colname="3"> Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion "Trick-Play". </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate() </span> </td> 
   <td colname="3"> Ruft die aktuell ausgewählte Wiedergaberate ab. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig() </span> </td> 
   <td colname="3"> Gibt die <span class="codeph"> MediaPlayerItemConfig </span> Instanz, die mit diesem Element verknüpft ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Medienressource</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> Gibt die diesem Element zugeordnete Medienressource zurück. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId() </span> </td> 
   <td colname="3"> Gibt die mit diesem Element verknüpfte Medienkennung zurück. Diese ID wird festgelegt, wenn das Element mit <span class="codeph"> MediaPlayerItemLoader.load </span>. </td> 
  </tr> 
 </tbody> 
</table>
