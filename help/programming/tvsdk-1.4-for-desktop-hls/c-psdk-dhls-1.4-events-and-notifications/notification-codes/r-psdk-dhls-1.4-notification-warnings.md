---
description: Diese Tabelle zeigt detaillierte Informationen zu WARN. Typbenachrichtigungen.
seo-description: Diese Tabelle zeigt detaillierte Informationen zu WARN. Typbenachrichtigungen.
seo-title: WARNUNGSBenachrichtigungscodes
title: WARNUNGSBenachrichtigungscodes
uuid: 1ce5be07-f5bf-443c-b907-9768633e1300
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# WARNUNGSBenachrichtigungscodes{#warning-notification-codes}

Diese Tabelle zeigt detaillierte Informationen zu WARN. Typbenachrichtigungen.

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

Die meisten Warnungen enthalten relevante Metadaten, z. B. die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, um anzugeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

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
   <td colname="5"> <p>Ein wiedergabebezogener Vorgang ist fehlgeschlagen, aber die Wiedergabe kann fortgesetzt werden. </p> </td> 
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
   <td colname="4"><span class="codeph"> HINTERGRUND_MANIFEST_WARNING_ERROR</span><span class="codeph"> HINTERGRUND_MANIFEST_WARNING_NAME</span> <span class="codeph"> BESCHREIBUNG</span> </td> 
   <td colname="5"> <p> Fehler beim Download des Hintergrundmanifests. Ein Fehler beim Aktualisieren des Hintergrundmanifests wird als TVSDK-Warnung ausgelöst und führt nicht dazu, dass die Wiedergabe angehalten wird. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_SEEK_WARNUNG</span> </td> 
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
   <td colname="5"> <p>Die AVE-Bibliothek der unteren Ebene hat einen Fehler ausgegeben. </p> <p>Detaillierte Informationen zu den Werten für diese Metadatenfelder finden Sie unter <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details zu den NATIVE_ERROR-Benachrichtigungen</a> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="4"><b>DRM</b> <p><span class="codeph"> NATIVE_SUBERROR_CODE</span><span class="codeph"> DRM_ERROR_STRING</span> </p> </td> 
   <td colname="5">DRM-Fehlercode und DRM-Serverfehlerzeichenfolge. Detaillierte Informationen zu den Werten für diese Metadatenfelder finden Sie unter <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details zu den NATIVE_ERROR-Benachrichtigungen</a> .
   </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Allgemein</b> </td> 
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
   <td colname="5"> <p>Markiert ein generisches Warnhinweis-Ereignis. Nicht tatsächlich ausgestellt von TVSDK. Es ist nur ein Marker für das Ende des Zahlencodes, der den Warnungscodes entspricht. </p> </td> 
  </tr> 
 </tbody> 
</table>

