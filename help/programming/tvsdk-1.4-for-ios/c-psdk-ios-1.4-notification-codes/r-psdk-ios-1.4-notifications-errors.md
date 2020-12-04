---
description: Diese Tabelle enthält detaillierte Informationen zu FEHLERTypbenachrichtigungen.
seo-description: Diese Tabelle enthält detaillierte Informationen zu FEHLERTypbenachrichtigungen.
seo-title: FEHLER-Benachrichtigungscodes
title: FEHLER-Benachrichtigungscodes
uuid: cea75277-7747-4f9b-ad59-98f9f1a5ac2f
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 5%

---


# FEHLER-Benachrichtigungscodes{#error-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu FEHLERTypbenachrichtigungen.

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

Die meisten Fehler enthalten relevante Metadaten, z. B. die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, um anzugeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
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
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 100000  </span> </td> 
   <td colname="2"><span class="codeph"> DRM_ERROR  </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> MAJOR_DRM_CODE  </span><span class="codeph"> MINOR_DRM_CODE  </span><span class="codeph"> BESCHREIBUNG  </span> </td> 
   <td colname="5"></td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Wiedergabe</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR  </span> </td> 
   <td colname="3"></td> 
   <td colname="4"></td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101001  </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_PLAYBACK_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG  </span><span class="codeph"> INTERNAL_ERROR- </span><span class="codeph"> URL  </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008  </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG</span> </td> 
   <td colname="5"> <p>Beim Durchführen eines Suchvorgangs ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009  </span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Beim Durchführen eines Pausenvorgangs ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101101  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> PLAYER_NOT_READY  </span> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>  </p> <p>  </p>
    <!-- workaround for PDF having too much negative kerning in column 2 --> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ungültige Ressource</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102000  </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_MEDIA_PLAYER_ITEM  </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Anzeigenverarbeitung</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_INVALID  </span> </td> 
   <td colname="3"> <span class="codeph"> AD_NOT_INSERTED</span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Die Anzeigenauflösung ist aufgrund eines ungültigen Ad-Metadaten-Formats fehlgeschlagen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="3"> <span class="codeph"> AD_NOT_INSERTED  </span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Die Phase der Anzeigenauflösung ist fehlgeschlagen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104006  </span> </td> 
   <td colname="2"><span class="codeph"> AD_UNERREICHBAR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Nativ</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106000  </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Ein iOS-Fehler auf niedriger Ebene ist aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Konfiguration</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107002  </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_VISIBILITY_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Beim Versuch, die Sichtbarkeit der CC-Tracks zu ändern, ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107003  </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_STYLING_ERROR  </span> </td> 
   <td colname="3"> <span class="codeph"> NATIVE_ERROR  </span> </td> 
   <td colname="4"> <p>Keines </p> </td> 
   <td colname="5"> <p>Beim Versuch, die Formatierungsoptionen für die CC-Tracks zu ändern, ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>iOS eindeutig</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170000  </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_VERSION_INCOMPATIBLE  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>Die HLS-Version der Anzeigen ist höher als die HLS-Version des Inhalts. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170001  </span> </td> 
   <td colname="2"><span class="codeph"> ARGUMENT_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>Argumentfehler </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170002  </span> </td> 
   <td colname="2"><span class="codeph"> M3U8_PARSER_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG  </span> </td> 
   <td colname="5"> <p>m3u8 konnte nicht analysiert werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170003  </span> </td> 
   <td colname="2"><span class="codeph"> WEBVTT_PARSER_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>Webvtt konnte nicht analysiert werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170004  </span> </td> 
   <td colname="2"><span class="codeph"> HLS_SEGMENT_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG  </span><span class="codeph"> URL  </span><span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Das Segment überschreitet die angegebene Bandbreite für die Variante. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170005  </span> </td> 
   <td colname="2"><span class="codeph"> MBR_MEDIASEQUENCE_OFFSYNC  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>Die Mediensequenznummer ist nicht auf allen HLS-Streams dieses MBR synchron. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170006  </span> </td> 
   <td colname="2"><span class="codeph"> MISSING_FILE_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG  </span><span class="codeph"> URL  </span><span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Fehlende Datei oder keine Antwort. </p> <p>HTTP 404: Datei nicht gefunden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170007  </span> </td> 
   <td colname="2"><span class="codeph"> AD_EMPTY_RESPONSE  </span> </td> 
   <td colname="3"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>Anzeigen konnten nicht abgerufen werden. Leere Antwort. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170008  </span> </td> 
   <td colname="2"><span class="codeph"> AD_TIMEOUT  </span> </td> 
   <td colname="3"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>Anzeigen konnten nicht abgerufen werden. Timeout-Fehler. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170009  </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> PLAYER_NOT_READY  </span> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>Fehler beim Ändern der Untertitelspur. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170010  </span> </td> 
   <td colname="2"><span class="codeph"> SITECATALYST_ERROR  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG  </span> </td> 
   <td colname="5"> <p>Site-Katalysator-Fehler. Siehe Beschreibung. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170011  </span> </td> 
   <td colname="2"><span class="codeph"> AD_ZIELGRUPPE_DURATION_INCOMPATIBLE  </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>Die ZIELGRUPPE der Anzeige ist höher als die ZIELGRUPPE DAUER des Inhalts. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>adID und source (URL) können über das `PTAdAsset` in den Benachrichtigungsmetadaten mit dem `AD_ASSET`-Schlüssel abgerufen werden.
