---
description: Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.
seo-description: Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.
seo-title: WARNUNGSBenachrichtigungscodes
title: WARNUNGSBenachrichtigungscodes
uuid: 32b54e6c-f107-4e8e-aad6-34e1057719b0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# WARNUNGSBenachrichtigungscodes {#warning-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.

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
   <td colname="1"><b>Anzeigenauflösung</b> </td> 
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
   <td colname="1"><span class="codeph"> 201002</span> </td> 
   <td colname="2"><span class="codeph"> AD_ASSET_FAILED_TO_LOAD</span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> AD_ASSET, INTERNAL_ERROR</span> </td> 
   <td colname="5"> <p>Beim Versuch, eine Werbeanzeige zu laden, ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201003</span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RETURNED_NO_ADS</span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> INTERNAL_ERROR, AD_ID, BESCHREIBUNG</span> </td> 
   <td colname="5"> <p>Die Anzeigenauflösung schlug aufgrund einer ungültigen VAST-URL oder weil keine Anzeige vom VAST-Wrapper zurückgegeben wurde. </p> </td> 
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
   <td colname="5"> <p>Die AVE-Bibliothek der unteren Ebene hat einen Fehler ausgegeben. </p> <p>Detaillierte Informationen zu den Werten für diese Metadatenfelder finden Sie unter <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> Details zu den NATIVE_ERROR-Benachrichtigungen</a> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="4"><b>DRM</b> <p><span class="codeph"> NATIVE_SUBERROR_CODE</span><span class="codeph"> DRM_ERROR_STRING</span> </p> </td> 
   <td colname="5"> DRM-Fehlercode und DRM-Serverfehlerzeichenfolge. Detaillierte Informationen zu den Werten für diese Metadatenfelder finden Sie unter <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> Details zu den NATIVE_ERROR-Benachrichtigungen</a> .</td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>TimeRangeCollection</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210000 </span> </td> 
   <td colname="2"><span class="codeph"> UNDEFINED_TIME_RANGES </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> Der Anzeigensignalisierungsmodus ist als benutzerdefinierter Bereich definiert, es sind jedoch keine Bereiche definiert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_TIME_RANGES </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p> Ein oder mehrere Zeitbereiche sind ungültig und werden ignoriert oder geändert. </p> <p> BESCHREIBUNG ist eine Zeichenfolge, die eine Beschreibung der ungültigen Bereiche enthält. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Trick-Modus</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 280000 </span> </td> 
   <td colname="2"><span class="codeph"> TRICKPLAY_RATE_CHANGE_FAIL</span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG</span> </td> 
   <td colname="5"> <p> Ratenänderung fehlgeschlagen. </p> </td> 
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

>[HINWEIS!] adID und source (URL) können über das PTAdAsset in den Benachrichtigungsmetadaten mit dem `AD_ASSET` Schlüssel abgerufen werden.
