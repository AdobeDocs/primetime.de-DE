---
description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
seo-description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
seo-title: MediaPlayer-Attribute für den Zugriff auf MediaResource-Informationen
title: MediaPlayer-Attribute für den Zugriff auf MediaResource-Informationen
uuid: d26f39d6-0a6b-4072-b99a-8767a511a846
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# MediaPlayer-Attribute für den Zugriff auf MediaResource-Informationen{#mediaplayer-attributes-to-access-mediaresource-information}

Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.

<table frame="all" colsep="1" rowsep="1" id="table_46225307CA5B4BB1869576E0B9141E38"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Zweck </th> 
   <th colname="2" class="entry"> Attribut </th> 
   <th colname="3" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Live-Stream </td> 
   <td colname="2"> <span class="codeph"> live </span> </td> 
   <td colname="3"> True, wenn der Stream live ist; false, wenn es VOD ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Untertitel </td> 
   <td colname="2"> <span class="codeph"> hasClosedCaptions </span> </td> 
   <td colname="3"> True, wenn Untertitel-Tracks verfügbar sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> closeCaptionsTracks </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren Untertitelspuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedClosedCaptionsTrack </span> </td> 
   <td colname="3"> Ruft die mit <span class="codeph"> selectClosedCaptionsTrack ausgewählte Untertitelspur ab </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Alternativaudio </td> 
   <td colname="2"> <span class="codeph"> hasAlternateAudio </span> </td> 
   <td colname="3"> <p>True, wenn der Stream über alternative Audiospuren verfügt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> audioTracks </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedAudioTrack </span> </td> 
   <td colname="3"> 
    <pre>
      Ruft die aktuell ausgewählte Audiospur ab, die mit <span class="codeph"> selectAudioTrack ausgewählt wurde </span>. 
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> Zeitgesteuerte Metadaten </td> 
   <td colname="2"> <span class="codeph"> hasTimedMetadata </span> </td> 
   <td colname="3"> True, wenn dem Stream Zeitmetadaten zugeordnet sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> timedMetadata </span> </td> 
   <td colname="3"> Bietet eine Liste der zeitgesteuerten Metadatenobjekte, die mit dem Stream verknüpft sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> Mehrere Profil (Bitraten) </td> 
   <td colname="2" morerows="1"> <span class="codeph"> profile </span> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="3"> Bietet eine Liste der mit diesem Stream verknüpften Bitrate-Profil. <p>Hinweis:  Sie können die Bitrate für jedes Profil sowie die Höhe und Breite des Profils abrufen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Medienressource </td> 
   <td colname="2"> <span class="codeph"> resource </span> </td> 
   <td colname="3"> Gibt die mit diesem Element verknüpfte Medienressource zurück. </td> 
  </tr> 
 </tbody> 
</table>

