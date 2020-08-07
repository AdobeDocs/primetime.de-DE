---
description: Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.
seo-description: Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.
seo-title: WARNING notification codes
title: WARNING notification codes
uuid: 136b5a65-b842-40fd-8ddd-efe01d73c388
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 3%

---


# WARNING notification codes{#warning-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu WARN-Typbenachrichtigungen.

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

Most warnings contain relevant metadata, for example, the URL of the resource that failed to download. Some notifications contain metadata to specify whether the problem occurred in the main video content, in the alternate audio content, or in an ad.

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Name </th> 
   <th colname="3" class="entry"> InnerNotification </th> 
   <th colname="4" class="entry"> Metadata Keys </th> 
   <th colname="5" class="entry"> Comments </th> 
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
   <td colname="5"> <p>An error has occurred when trying to load an ad creative. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201003</span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_ RETURNED_NO_ADS</span> </td> 
   <td colname="3"> <p>None </p> </td> 
   <td colname="4"><span class="codeph"> INTERNAL_ERROR, AD_ID,DESCRIPTION</span> </td> 
   <td colname="5"> <p>Ad resolving failed because of an invalid VAST URL or because no ad was returned from the VAST wrapper. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Background manifests</b> </td> 
   <td colname="2"> </td>
   <td colname="3"> </td>
   <td colname="4"> </td>
   <td colname="5"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204000 </span> </td> 
   <td colname="2"><span class="codeph"> BACKGROUND_MANIFEST_ WARNING</span> </td> 
   <td colname="3"> <p>None </p> </td> 
   <td colname="4"><span class="codeph"> HINTERGRUND_MANIFEST_WARNING_ERROR</span><span class="codeph"> HINTERGRUND_MANIFEST_WARNING_NAME</span> <span class="codeph"> BESCHREIBUNG</span> </td> 
   <td colname="5"> <p> Fehler beim Download des Hintergrundmanifests. Ein Fehler beim Aktualisieren des Hintergrundmanifests wird als TVSDK-Warnung ausgelöst und führt nicht dazu, dass die Wiedergabe angehalten wird. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_SEEK_WARNUNG</span> </td> 
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
   <td colname="4"> <p>None </p> </td> 
   <td colname="5"> <p>AD was not inserted on the stream. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270002 </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_AUDIOONLY_MISSING </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Anzeige enthält nicht den Stream "Nur Audio" </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_MATCHING_BITRATE_MISSING </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="4"> <p>None </p> </td> 
   <td colname="5"> <p>Für die aktuelle Bitrate des Inhalts wurde kein übereinstimmender Anzeigenstream gefunden. </p> <p>  </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270005 </span> </td> 
   <td colname="2"><span class="codeph"> AVASSET_FAILED_TO_CREATE </span> </td> 
   <td colname="3"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="4"> <p>None </p> </td> 
   <td colname="5"> <p>Error at creating the AVAsset. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270006 </span> </td> 
   <td colname="2"><span class="codeph"> SITECATALYST_WARNING </span> </td> 
   <td colname="3"> <p>None </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Warnung: Siehe Beschreibung der SiteCatalyst-Warnung. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270007 </span> </td> 
   <td colname="2"><span class="codeph"> NETWORK_ERROR </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> <p>Fehler beim Abrufen von Daten aus dem Netzwerk. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270002</span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_AUDIOONLY_MISSING</span> </td> 
   <td colname="3"> <p>None </p> </td> 
   <td colname="4"><span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>Die Audiowiedergabe für diese Anzeige kann nicht gehört werden, da sie fehlt </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270003</span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_MATCHING_BITRATE_MISSING</span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>The matching bitrate is missing. </p> <p>  </p>
    <!-- workaround for PDF having too much negative kerning in column 2 --> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>adID and source (URL) can be retrieved through the PTAdAsset in the notification metadata with the `AD_ASSET` key.
