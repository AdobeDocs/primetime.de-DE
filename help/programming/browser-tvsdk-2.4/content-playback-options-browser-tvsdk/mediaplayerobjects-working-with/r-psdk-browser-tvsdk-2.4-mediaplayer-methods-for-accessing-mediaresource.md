---
description: Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.
title: MediaPlayer-Attribute für den Zugriff auf MediaResource-Informationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# MediaPlayer-Attribute für den Zugriff auf MediaResource-Informationen{#mediaplayer-attributes-to-access-mediaresource-information}

Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.

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
   <td colname="3"> True , wenn der Stream live ist, false , wenn es VOD ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Geschlossene Untertitel </td> 
   <td colname="2"> <span class="codeph"> hasClosedCaptions </span> </td> 
   <td colname="3"> True , wenn geschlossene Untertitelspuren verfügbar sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> closedCaptionsTracks </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren Tracks mit geschlossenen Untertiteln. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedClosedCaptionsTrack </span> </td> 
   <td colname="3"> Ruft die Untertitelspur ab, die mit <span class="codeph"> selectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Alternativaudio </td> 
   <td colname="2"> <span class="codeph"> hasAlternateAudio </span> </td> 
   <td colname="3"> <p>True , wenn der Stream alternative Audiospuren hat. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> audioTracks </span> </td> 
   <td colname="3"> Bietet eine Liste der verfügbaren alternativen Audiospuren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedAudioTrack </span> </td> 
   <td colname="3"> 
    <pre>
      Ruft den derzeit ausgewählten Audio-Track ab, der mit 
     <span class="codeph"> selectAudioTrack </span>. 
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> Zeitgesteuerte Metadaten </td> 
   <td colname="2"> <span class="codeph"> hasTimedMetadata </span> </td> 
   <td colname="3"> True , wenn dem Stream zeitgesteuerte Metadaten zugeordnet sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> timedMetadata </span> </td> 
   <td colname="3"> Stellt eine Liste der zeitgesteuerten Metadatenobjekte bereit, die mit dem Stream verknüpft sind. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> Mehrere Profile (Bitraten) </td> 
   <td colname="2" morerows="1"> <span class="codeph"> profiles </span> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="3"> Bietet eine Liste der mit diesem Stream verknüpften Bitratenprofile. <p>Hinweis: Sie können die Bitrate für jedes Profil sowie die Höhe und Breite des Profils abrufen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Medienressource </td> 
   <td colname="2"> <span class="codeph"> resource </span> </td> 
   <td colname="3"> Gibt die mit diesem Element verknüpfte Medienressource zurück. </td> 
  </tr> 
 </tbody> 
</table>
