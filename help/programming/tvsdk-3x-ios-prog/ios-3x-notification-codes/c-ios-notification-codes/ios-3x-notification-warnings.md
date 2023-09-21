---
description: Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.
title: WARNUNGSBenachrichtigungscodes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# WARNUNGSBenachrichtigungscodes {#warning-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

Die meisten Warnungen enthalten relevante Metadaten, beispielsweise die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, die angeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Code</b></th> 
   <th colname="2" class="entry"><b>Name</b></th> 
   <th colname="3" class="entry"><b>InnerNotification&gt;/b&gt;</th> 
   <th colname="4" class="entry"><b>Metadatenschlüssel</b></th> 
   <th colname="5" class="entry"><b>Kommentare</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Anzeigenauflösung</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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
   <td colname="4"><span class="codeph"> INTERNAL_ERROR, AD_ID, DESCRIPTION</span> </td> 
   <td colname="5"> <p>Die Anzeigenauflösung schlug aufgrund einer ungültigen VAST-URL oder weil vom VAST-Wrapper keine Anzeige zurückgegeben wurde, fehl. </p> </td> 
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
   <td colname="5"> <p></p> </td> 
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
   <td colname="5"> Der Anzeigesignalmodus ist als benutzerdefinierter Bereich definiert, es sind jedoch keine Bereiche definiert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_TIME_RANGES </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p> Ein oder mehrere Zeitbereiche sind ungültig und werden ignoriert oder geändert. </p> <p> BESCHREIBUNG ist eine Zeichenfolge, die eine Beschreibung der ungültigen Bereiche enthält. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>iOS-spezifisch</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_NOT_READY </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Anzeige wurde nicht in den Stream eingefügt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270002 </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_AUDIOONLY_MISSING </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Anzeige enthält keinen reinen Audio-Stream </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_MATCHING_BITRATE_MISSING </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Für die aktuelle Bitrate des Inhalts wurde kein übereinstimmender Anzeigen-Stream gefunden. </p> <p>  </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270005 </span> </td> 
   <td colname="2"><span class="codeph"> AVASSET_FAILED_TO_CREATE </span> </td> 
   <td colname="3"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Fehler beim Erstellen des AVAset. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270006 </span> </td> 
   <td colname="2"><span class="codeph"> SITECATALYST_WARNING </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Warnung: Siehe sitecatalyst-Warnbeschreibung. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270007 </span> </td> 
   <td colname="2"><span class="codeph"> NETWORK_ERROR </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> <p>Fehler beim Abrufen von Daten aus dem Netzwerk. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>adID und Quelle (URL) können über das PTAdAsset in den Benachrichtigungsmetadaten mit der `AD_ASSET` Schlüssel.
>
>Die [] -Attribut gibt einen optionalen Schlüssel für die Benachrichtigung an.
