---
description: Diese Tabelle enthält detaillierte Informationen zu INFO-Typbenachrichtigungen.
title: INFO-Benachrichtigungscodes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 4%

---

# INFO-Benachrichtigungscodes{#info-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu INFO-Typbenachrichtigungen.

## Abschnittstitel {#section_ED4302E363AE48CBA2C3E0B71AE612D8}

Die meisten Informationsbenachrichtigungen enthalten relevante Metadaten, beispielsweise die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, die angeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Name </th> 
   <th colname="3" class="entry"> Innen-Benachrichtigung </th> 
   <th colname="4" class="entry"> Metadatenschlüssel </th> 
   <th colname="5" class="entry"> Kommentare </th> 
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
   <td colname="2"><span class="codeph"> PLAYBACK_START </span> </td> 
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
   <td colname="2"><span class="codeph"> SEEK_START </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> Ein Suchvorgang wurde eingeleitet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_COMPLETE </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> Ein Suchvorgang ist abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_CHANGE </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <span class="codeph"> CONTENT_ID</span> <span class="codeph"> CURRENT_MEDIA_TIME</span> </td> 
   <td colname="5"> Die aktuelle Wiedergabezeit hat den Rand zwischen Haupt- und Alternativinhalt überschritten. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE </span> </td> 
   <td colname="3"> <p>Jede FEHLERbenachrichtigung. </p> </td> 
   <td colname="4"><span class="codeph"> STAND </span> </td> 
   <td colname="5"> Der Player-Status hat sich geändert. Wenn der Status FEHLER ist, ist die innere Benachrichtigung das Fehlerbenachrichtigungsobjekt, das den Wechsel zum FEHLER-Status ausgelöst hat. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300100 </span> </td> 
   <td colname="2"><span class="codeph"> LOAD_INFO_AVAILABLE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <span class="codeph"> FRAGMENT_URL</span> <span class="codeph"> FRAGMENT_SIZE</span> <span class="codeph"> FRAGMENT_DOWNLOAD_DURATION</span> <span class="codeph"> PERIOD_INDEX</span> </td> 
   <td colname="5"> Enthält Informationen zur Art und Weise, wie Videosegmente heruntergeladen werden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300101 </span> </td> 
   <td colname="2"><span class="codeph"> VIDEO_SIZE_CHANGED </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <span class="codeph"> HÖHE</span> <p><span class="codeph"> BREITE</span> </p> </td> 
   <td colname="5"> Die Größe des Videowiedergabefensters hat sich geändert. </td> 
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
   <td colname="4"><span class="codeph"> BITRATE </span><span class="codeph"> CURRENT_MEDIA_TIME </span> </td> 
   <td colname="5"> Die Bitrate des Videos hat sich geändert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Anzeigenverarbeitung </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303000 </span> </td> 
   <td colname="2"><span class="codeph"> TIMELINE_CHANGE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span><span class="codeph"> PERIOD_INDEX </span> </td> 
   <td colname="5"> Die Timeline wurde geändert (z. B. wurden alternative Inhalte hinzugefügt oder entfernt). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_PLACEMENT_COMPLETE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <span class="codeph"> PROPOSED_AD_BREAK</span> <span class="codeph"> ACCEPTED_AD_BREAK</span> </td> 
   <td colname="5"> Eine geplante Werbeunterbrechung wurde von TVSDK akzeptiert und (vollständig oder nur teilweise) auf die Wiedergabescheitleiste gesetzt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303002 </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_START </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK </span> </td> 
   <td colname="5"> Die Wiedergabe einer bestimmten Werbeunterbrechung wurde gestartet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_COMPLETE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK </span> </td> 
   <td colname="5"> Die Wiedergabe einer bestimmten Werbeunterbrechung wurde abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303004 </span> </td> 
   <td colname="2"><span class="codeph"> AD_START </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> Die Wiedergabe einer bestimmten Anzeige wurde gestartet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_COMPLETE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> Die Wiedergabe einer bestimmten Anzeige ist abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303006 </span> </td> 
   <td colname="2"><span class="codeph"> AD_PROGRESS </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> <span class="codeph"> FORTSCHRITT</span> </td> 
   <td colname="5"> Die Wiedergabe einer bestimmten Anzeige hat einen bestimmten Prozentsatz dieser Anzeige erreicht. </td> 
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
   <td colname="4"><span class="codeph"> TRACK_ID </span><span class="codeph"> CURRENT_MEDIA_TIME </span> </td> 
   <td colname="5"> <p>Der Audio-Track hat sich geändert. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 305000 </span> </td> 
   <td colname="2"><span class="codeph"> DRM_METADATA_AVAILABLE </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> PREFETCH_TIMESTAMP </span> </td> 
   <td colname="5"> <p>Es sind neue DRM-Daten verfügbar. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Generisch</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 399999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_INFO </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Markiert ein allgemeines Informationsereignis. Nicht tatsächlich von TVSDK ausgestellt. Es ist nur eine Markierung für das Ende des numerischen Codes, der TVSDK-Informationsereignissen entspricht. </p> </td> 
  </tr> 
 </tbody> 
</table>
