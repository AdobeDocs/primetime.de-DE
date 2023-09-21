---
description: Diese Tabelle enthält detaillierte Informationen zu FEHLER-Benachrichtigungen.
title: FEHLER-Benachrichtigungscodes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 4%

---

# FEHLER-Benachrichtigungscodes{#error-notification-codes}

Diese Tabelle enthält detaillierte Informationen zu FEHLER-Benachrichtigungen.

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

Die meisten Fehler enthalten relevante Metadaten, beispielsweise die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, die angeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

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
   <td colname="1"><span class="codeph"> 100000 </span> </td> 
   <td colname="2"><span class="codeph"> DRM_ERROR </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> MAJOR_DRM_CODE </span><span class="codeph"> MINOR_DRM_CODE </span><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5">Siehe auch 106000 (
     <span class="codeph"> NATIVE_ERROR</span>).
   </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Wiedergabe</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>Beim Herunterladen eines Fragments oder Segments (sowohl Video als auch Audio) ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101006 </span> </td> 
   <td colname="2"><span class="codeph"> SECURITY_ERROR </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008</span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> <span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Ausführen eines Pausenvorgangs ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> DESIRED_SEEK_POSITION </span><span class="codeph"> DESIRED_SEEK_PERIOD </span> </td> 
   <td colname="5"> <p>Beim Ausführen eines Suchvorgangs ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102 </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Abrufen von Informationen zu einem Inhaltszeitraum ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103 </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Versuch, die Wiedergabeposition abzurufen, ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104 </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Versuch, die QOS-Informationen abzurufen, ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200 </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> <p>Beim Versuch, Daten herunterzuladen, ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ungültige Ressource </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102100 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_LOAD_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span><span class="codeph"> RESSOURCE </span> </td> 
   <td colname="5"> <p>Beim Laden eines Ressourcenelements ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_PLACEMENT_FAILED </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span> </td> 
   <td colname="5"> <p>Beim Platzieren einer Ressource in der Wiedergabeschlüssel ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Anzeigenverarbeitung </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104000 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AD_METADATA_INVALID </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> AD_RESOLVER_SERVER_UNREACHABLE </span> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> Keines </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_INVALID </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>Die Anzeigenauflösung schlug aufgrund eines ungültigen Anzeigenmetadatenformats fehl. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="5"> <p>Das Anzeigen-Plugin konnte Anzeigen nicht auflösen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL </span> </td> 
   <td colname="3">Keines</td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> <p>Die Anzeigeauflösungsphase ist fehlgeschlagen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104006 </span> </td> 
   <td colname="2"><span class="codeph"> AD_UNREACHABLE </span> </td> 
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
   <td colname="1"><span class="codeph"> 106000 </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> RUNTIME_CODE</span> <span class="codeph"> RUNTIME_CODE_MESSAGE</span> <span class="codeph"> RESOURCE_URL</span> <span class="codeph"> RESOURCE_TYPE</span> <span class="codeph"> RESOURCE_ID</span> <p><b>DRM-Details:</b> </p> <span class="codeph"> DRM_ERROR_STRING</span> <span class="codeph"> RUNTIME_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>Die AVE-Bibliothek der unteren Ebene hat einen Fehler ausgegeben. </p> <p>Siehe <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details für NATIVE_ERROR-Benachrichtigungen</a> für Informationen zu den Werten für diese Metadatenschlüssel. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Instanziieren der AVE-Bibliothek auf niedriger Ebene ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Freigeben der AVE-Bibliothek auf niedriger Ebene ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Freigeben der von der AVE-Bibliothek verwendeten GPU-Ressourcen ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESET_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Zurücksetzen der AVE-Bibliothek ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_VIEW_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Anhängen einer Ansicht an die AVE-Bibliothek ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Alternativaudio</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 109000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_ERROR </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="4"><span class="codeph"> AUDIO_TRACK_NAME </span><span class="codeph"> AUDIO_TRACK_LANGUAGE </span> </td> 
   <td colname="5"> <p>Es ist ein Fehler im Zusammenhang mit einem Audio-Track aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Generisch</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 199999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> <p>Markiert ein allgemeines Fehlerereignis. Nicht tatsächlich von TVSDK ausgestellt. Es handelt sich lediglich um eine Markierung für das Ende des Bereichs numerischer Codes, die TVSDK-Fehlerereignissen entsprechen. </p> </td> 
  </tr> 
 </tbody> 
</table>
