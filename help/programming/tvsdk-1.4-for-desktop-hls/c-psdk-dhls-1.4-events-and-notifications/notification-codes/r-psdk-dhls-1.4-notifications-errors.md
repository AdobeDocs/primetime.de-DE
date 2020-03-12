---
description: Diese Tabelle enthält detaillierte Informationen zu FEHLERTypbenachrichtigungen.
seo-description: Diese Tabelle enthält detaillierte Informationen zu FEHLERTypbenachrichtigungen.
seo-title: FEHLER-Benachrichtigungscodes
title: FEHLER-Benachrichtigungscodes
uuid: 50624782-3d0b-4ac4-b883-355c1f7e9bff
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

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
   <td colname="1"><span class="codeph"> 100000 </span> </td> 
   <td colname="2"><span class="codeph"> DRM_ERROR </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> MAJOR_DRM_CODE </span><span class="codeph"> MINOR_DRM_CODE </span><span class="codeph"> -BESCHREIBUNG </span> </td> 
   <td colname="5">Siehe auch 106000 ( <span class="codeph"> NATIVE_ERROR</span>).
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
   <td colname="5"> <p>Beim Durchführen eines Pausenvorgangs ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> DESIRED_SEEK_POSITION </span><span class="codeph"> DESIRED_SEEK_PERIOD </span> </td> 
   <td colname="5"> <p>Beim Durchführen eines Suchvorgangs ist ein Fehler aufgetreten. </p> </td> 
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
   <td colname="5"> <p>Beim Versuch, die Servicequalitätsinformationen abzurufen, ist ein Fehler aufgetreten. </p> </td> 
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
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span><span class="codeph"> RESSOURCEN </span> </td> 
   <td colname="5"> <p>Beim Laden eines Ressourcenelements ist ein Fehler aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_PLACEMENT_FAILED </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span> </td> 
   <td colname="5"> <p>Beim Platzieren einer Ressource in der Zeitleiste der Wiedergabe ist ein Fehler aufgetreten. </p> </td> 
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
   <td colname="3"><span class="codeph"> AD_METADATA_INVALID </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> AD_RESOLVER_SERVER_UNERREICHBAR </span> </td> 
   <td colname="4"> Keines </td> 
   <td colname="5"> Keines </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_INVALID </span> </td> 
   <td colname="3"> <p>Keines </p> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>Die Anzeigenauflösung ist aufgrund eines ungültigen Ad-Metadaten-Formats fehlgeschlagen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="5"> <p>Anzeigen-Plugin konnte keine Anzeigen auflösen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL </span> </td> 
   <td colname="3">Keines</td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> <p>Die Phase der Anzeigenauflösung ist fehlgeschlagen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104006 </span> </td> 
   <td colname="2"><span class="codeph"> AD_UNERREICHBAR </span> </td> 
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
   <td colname="4"><span class="codeph"> RUNTIME_CODE</span> RUNTIME_CODE_MESSAGE <span class="codeph"> RESOURCE_URL</span> RESOURCE_TYPE <span class="codeph"></span> <span class="codeph"></span> <span class="codeph"> RESOURCE_ID</span> <p><b>DRM-Details:</b> </p> <span class="codeph"> DRM_ERROR_STRING</span><span class="codeph"> RUNTIME_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>Die AVE-Bibliothek der unteren Ebene hat einen Fehler ausgegeben. </p> <p>Informationen zu den Werten für diese Metadatenschlüssel finden Sie unter <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details zu den NATIVE_ERROR-Benachrichtigungen</a> . </p> </td> 
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
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_FEHLER </span> </td> 
   <td colname="3"> Keines </td> 
   <td colname="4"><span class="codeph"> BESCHREIBUNG </span> </td> 
   <td colname="5"> <p>Beim Freigeben der Bibliothek der unteren Ebene in AVE ist ein Fehler aufgetreten. </p> </td> 
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
   <td colname="2"><span class="codeph"> ENGINE_SET_ANSICHT_ERROR </span> </td> 
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
   <td colname="5"> <p>Es ist ein Fehler im Zusammenhang mit einer Audiospur aufgetreten. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Allgemein</b> </td> 
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
   <td colname="5"> <p>Markiert ein generisches Ereignis mit einem Fehler. Nicht tatsächlich ausgestellt von TVSDK. Es ist nur ein Marker für das Ende des Bereichs der numerischen Ereignisse, die TVSDK-Fehler. </p> </td> 
  </tr> 
 </tbody> 
</table>

