---
description: Diese Tabelle enthält detaillierte Informationen zu WARN. Typbenachrichtigungen.
title: WARNUNGSBenachrichtigungscodes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 2%

---

# WARNUNGSBenachrichtigungscodes{#warning-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu WARN. Typbenachrichtigungen.

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

Die meisten Warnungen enthalten relevante Metadaten, beispielsweise die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, die angeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Name </th> 
   <th colname="3" class="entry"> InnerNotification </th> 
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
   <td colname="1"><span class="codeph"> 200000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_OPERATION_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AUDIO_TRACK_ERROR </span><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Ein wiedergabebezogener Vorgang ist fehlgeschlagen, die Wiedergabe kann jedoch fortgesetzt werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Anzeigenauflösung </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201000 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> RESOURCE_PLACEMENT_FAILED </span><span class="codeph"> AD_RESOLVER_METADATA_INVALID </span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Der Anzeigenauflöser konnte den Anzeigeninhalt nicht auflösen/einfügen. Die Wiedergabe kann fortgesetzt werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Hintergrundmanifeste</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204000 </span> </td> 
   <td colname="2"><span class="codeph"> HINTERGRUND_MANIFEST_WARNUNG</span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> HINTERGRUND_MANIFEST_WARNING_ERROR</span> <span class="codeph"> HINTERGRUND_MANIFEST_WARNING_NAME</span> <span class="codeph"> BESCHREIBUNG</span> </td> 
   <td colname="5"> <p> Fehler beim Herunterladen des Hintergrundmanifests. Jedes Problem beim Aktualisieren des Hintergrundmanifests wird als TVSDK-Warnung gesendet und führt nicht dazu, dass die Wiedergabe angehalten wird. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_SEEK_WARNING</span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG</span> </td> 
   <td colname="5"> <p> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Nativ</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"><span class="codeph"> 209100 </span> </td> 
   <td colname="2" morerows="1"><span class="codeph"> NATIVE_WARNING </span> </td> 
   <td colname="3" morerows="1"> <p>Keines </p> </td> 
   <td colname="4"><b>AVE</b> <p><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> NATIVE_ERROR_NAME </span><span class="codeph"> BESCHREIBUNG </span> </p> </td> 
   <td colname="5"> <p>Die AVE-Bibliothek der unteren Ebene hat einen Fehler ausgegeben. </p> <p>Siehe <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details für NATIVE_ERROR-Benachrichtigungen</a> für detaillierte Informationen zu den Werten für diese Metadatenfelder. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="4"><b>DRM</b> <p><span class="codeph"> NATIVE_SUBERROR_CODE</span> <span class="codeph"> DRM_ERROR_STRING</span> </p> </td> 
   <td colname="5">DRM-Fehlercode und DRM-Server-Fehlerzeichenfolge. Siehe <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details für NATIVE_ERROR-Benachrichtigungen</a> für detaillierte Informationen zu den Werten für diese Metadatenfelder.
   </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Generisch</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 299999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_WARNING </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Markiert ein allgemeines Warnereignis. Nicht tatsächlich von TVSDK ausgestellt. Es handelt sich lediglich um eine Markierung für das Ende des numerischen Codes, der Warnungsereignissen entspricht. </p> </td> 
  </tr> 
 </tbody> 
</table>
