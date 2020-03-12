---
description: Diese Tabelle enthält detaillierte Informationen zu INFO-Typbenachrichtigungen.
seo-description: Diese Tabelle enthält detaillierte Informationen zu INFO-Typbenachrichtigungen.
seo-title: INFO-Benachrichtigungscodes
title: INFO-Benachrichtigungscodes
uuid: 21297863-dac1-45a4-ac9d-309d1f746f8b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# INFO-Benachrichtigungscodes {#info-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu INFO-Typbenachrichtigungen.

Die meisten Informationsbenachrichtigungen enthalten relevante Metadaten, z. B. die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, um anzugeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Code</b></th> 
   <th colname="2" class="entry"><b>Name</b></th> 
   <th colname="3" class="entry"><b>Innen-Benachrichtigung</b></th> 
   <th colname="4" class="entry"><b>Metadatenschlüssel</b></th> 
   <th colname="5" class="entry"><b>Kommentare</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Wiedergabe</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_BEGINN </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> Die Wiedergabe wurde gestartet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300001 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_COMPLETE </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> Die Wiedergabe ist abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300002 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_BEGINN </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <p> Keines </p> </td> 
   <td colname="5"> Ein Suchvorgang wurde initiiert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_COMPLETE </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> Ein Suchvorgang wurde abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> Der Player-Status hat sich geändert. Wenn der Status FEHLER ist, ist die innere Benachrichtigung das Fehlerbenachrichtigungsobjekt, das den Wechsel zum FEHLER-Status ausgelöst hat. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Adaptive Bitraten (ABR)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 302000 </span> </td> 
   <td colname="2"><span class="codeph"> BITRATE_CHANGE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BITRAT </span> </td> 
   <td colname="5"> Die Bitrate des Videos änderte sich. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Spätbindendes Audio (LBA)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 304000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Die Audiospur wurde geändert. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Untertitel</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 307000 </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Die Untertitelspur wurde geändert. </p> </td> 
  </tr> 
 </tbody> 
</table>