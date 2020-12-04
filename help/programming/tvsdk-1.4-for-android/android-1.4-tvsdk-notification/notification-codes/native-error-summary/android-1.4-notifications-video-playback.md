---
description: Die Video Encoder-Schnittstelle der AVE gibt diese Videowiedergabebenachrichtigungen im Metadatenobjekt NATIVE_ERROR zurück.
seo-description: Die Video Encoder-Schnittstelle der AVE gibt diese Videowiedergabebenachrichtigungen im Metadatenobjekt NATIVE_ERROR zurück.
seo-title: NATIVE_ERROR-Werte für die Videowiedergabe
title: NATIVE_ERROR-Werte für die Videowiedergabe
uuid: fbc08ecd-2e28-41ad-955b-557358bccdc8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 6%

---


# NATIVE_ERROR: Videowiedergabewerte{#native-error-video-playback-values}

Die Video Encoder-Schnittstelle der AVE gibt diese Videowiedergabebenachrichtigungen im Metadatenobjekt NATIVE_ERROR zurück.

<table> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Wert für den Metadatenschlüssel NATIVE_ERROR_CODE </th> 
   <th colname="col2" class="entry"> Wert für den Metadatenschlüssel NATIVE_ERROR_NAME </th> 
   <th colname="col3" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> Ende des Zeitraums. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> ERFOLG</span> </td> 
   <td colname="col3"> Vorgang erfolgreich. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> Asynchroner Vorgang. Der Antrag wurde gestellt. Erfolgs-/Fehlerinformationen stehen später zur Verfügung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> Vorgang aufgrund der Dateiende-Bedingung (EOF) nicht möglich. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> Der Decoder ist zur Laufzeit fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Hardwaredecoder konnte nicht geöffnet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND  </span> </td> 
   <td colname="col3"> Die Ressource kann nicht gefunden werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR  </span> </td> 
   <td colname="col3"> Allgemeiner Fehler. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR  </span> </td> 
   <td colname="col3"> Eine Fehlerbedingung, von der die Video-Engine nicht wiederhergestellt werden kann. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE  </span> </td> 
   <td colname="col3"> Netzwerkfehler beim Versuch der Wiederherstellung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE  </span> </td> 
   <td colname="col3"> Die Größe der Ressource kann nicht bestimmt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTITED  </span> </td> 
   <td colname="col3"> Funktion nicht implementiert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY  </span> </td> 
   <td colname="col3"> Nicht genügend Arbeitsspeicher. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR  </span> </td> 
   <td colname="col3"> Fehler beim Parsen der Mediendatei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN  </span> </td> 
   <td colname="col3"> Die Ressource hat eine Größe, aber sie ist unbekannt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW  </span> </td> 
   <td colname="col3"> Unterlaufbedingung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG  </span> </td> 
   <td colname="col3"> Konfiguration wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION  </span> </td> 
   <td colname="col3"> Vorgang wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT  </span> </td> 
   <td colname="col3"> Noch nicht initialisiert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER  </span> </td> 
   <td colname="col3"> Ungültiger Parameter. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> Vorgang nicht zulässig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> Der Vorgang ist nur während der Pause zulässig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> Der Vorgang kann nicht für reinen Audiodateien verwendet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> Der vorherige Suchvorgang wird noch ausgeführt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED  </span> </td> 
   <td colname="col3"> Ressource nicht angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> Der angegebene Wert liegt außerhalb des zulässigen Bereichs. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> Ungültige Suchzeit. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> Die angegebene Datei entspricht nicht der erwarteten Syntax. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> Eine wesentliche Komponente konnte nicht erstellt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> DRM-Kontext konnte nicht erstellt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> CONTAINER_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> Container-Typ wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> Suche fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Nicht unterstützter Codec. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNVERFÜGBAR</span> </td> 
   <td colname="col3"> Netzwerk ist nicht verfügbar. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> Fehler beim Abrufen von Daten aus dem Netzwerk. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> ÜBERLAUF</span> </td> 
   <td colname="col3"> Überlauf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_PROFIL_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Nicht unterstütztes Video-Profil. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> Ein Vorgang wurde für einen HOLD-Zeitraum oder einen Zeitraum versucht, der noch nicht geladen wurde. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> Die angegebene Ersetzungsdauer ist ungültig oder erstreckt sich über das Ende des Streams hinaus. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> CALLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> API kann nicht aus dem falschen Thread aufgerufen werden. Meistens für API-Elemente, die nur aus dem Main-Thread aufgerufen werden sollten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> Fragmentlesefehler. Kein Failover vorhanden. Engine versucht, das nächste Fragment zu lesen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> ABGESCHLOSSEN</span> </td> 
   <td colname="col3"> Der Vorgang wurde durch einen expliziten Abort- oder Destroy-Aufruf abgebrochen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> Diese Version des HLS-Mediums kann nicht wiedergegeben werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> Kann nicht übersprungen werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> Beim HTTP-Download ist ein Timeout aufgetreten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN  </span> </td> 
   <td colname="col3"> Die Netzwerkverbindung des Benutzers ist nicht verfügbar. Die Wiedergabe kann jeden Moment unterbrochen werden und wird fortgesetzt, sobald die Verbindung verfügbar ist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_PROFIL</span> </td> 
   <td colname="col3"> Es wurde kein nutzbares Bitrate-Profil im Stream gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> Das Manifest hat eine ungültige Unterschrift. Der Manifestsignierungstest ist fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> Wiedergabeliste kann nicht geladen werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> In einer Einfüge-API angegebene Ersetzung konnte nicht erfolgreich durchgeführt werden. Das bedeutet, dass die Einfügung erfolgreich war, die Ersetzung jedoch nicht. Der Austausch kann fehlschlagen, wenn das zu ersetzende Manifest aus der Zeitleiste entfernt wurde. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_PROFIL</span> </td> 
   <td colname="col3"> DRM wechselt zu einem asymmetrischen Profil. Es wird erwartet, dass alle Profil in ihrer Dauer ausgerichtet werden. Andernfalls wird diese Warnung ausgegeben und es kann zu Sprüngen bei der Wiedergabe kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> Es wird erwartet, dass das Live-Fenster nur vorwärts geht. Andernfalls wird diese Warnung ausgegeben und das Fenster wird nicht gelesen. Aus diesem Grund kann es bei der Wiedergabe zu Sprüngen (oder Stopp/Long Pause) kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> Das Live-Fenster wurde über den aktuellen Zeitraum hinaus verschoben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> Die vom HTTP-Server gemeldete Inhaltslänge entsprach nicht der tatsächlichen Mediengröße. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> Der Medienleser kann keine weiteren Informationen lesen, da er die mit der setHoldAt-API festgelegte Zeit erreicht hat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD  </span> </td> 
   <td colname="col3"> Der Medienleser kann keine Segmente laden, da er das Ende des Live-Fensters erreicht hat. Das Laden des Segments wird fortgesetzt, wenn der Server neue Medien in das Live-Fenster einfügt. Dieser Status wird normalerweise erreicht, wenn: 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48">bufferTime ist zu hoch (gleich oder höher als die Live-Fensterdauer). </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">Eine Kombination aus einer oder mehreren der API zum Einfügen/Löschen ersetzte mehr Medien als hinzugefügt. </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">Der nächste Zeitraum ist ein Live-Zeitraum mit einem ausstehenden Medienaustausch (aufgrund des InsertBy-API-Aufrufs) </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING  </span> </td> 
   <td colname="col3"> Das Audio- und Videointeragieren in den Medien wird nicht ordnungsgemäß ausgeführt. Dies ist ein Verpackungsfehler. Die Warnung wird ausgelöst, wenn der Unterschied zwei Sekunden überschreitet. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> Die HLS-Wiedergabe wurde im Flash Player nicht aktiviert. Siehe AuthorizedFeatures.enableHLSPlayback. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> Der Decoder hat ein schlechtes Beispiel erhalten, das nicht dekodiert werden kann. Dies ist in der Regel kein fataler Fehler, deutet aber darauf hin, dass es möglicherweise Fehler im Audio/Video gibt. Zu viele Instanzen dieses Fehlers deuten auf eine fehlerhafte Kodierung oder fehlerhafte Datei hin. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> Nach dem Start der Wiedergabe sollte der Bereich "Einfügen/Ersetzen"den Lesekopf nicht enthalten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> Einfügungen nach dem Rollen sind auf einem Live-Datenträger nicht zulässig. Sie sind jedoch zulässig, nachdem der Server die Medien als abgeschlossen markiert hat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> Ein sehr seltenes Thema, das nie passieren sollte. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> Der Stream entspricht nicht der Verpackungsempfehlung, immer H264 SPS/PPS in einen AVCC zu setzen. Probleme mit der Suche/Wiedergabe werden möglicherweise angezeigt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> In der Einfüge-API angegebene Ersetzung wurde nur teilweise vorgenommen. Dies geschieht, wenn replaceDuration sich über die Zeitschienendauer erstreckt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> Beim Laden der Wiedergabeliste für Darstellungen ist ein Fehler aufgetreten. Dies gilt nur für AVE, nicht für FlashPlayer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> Operation tut nichts. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> Das Segment kann nicht wiedergegeben werden und wird bei einem Fehler übersprungen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> Inkompatibler Rendermodus. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> Das in der URL verwendete Webprotokoll wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 69 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR_INCOMPATIBLE_VERSION</span> </td> 
   <td colname="col3"> Fehler beim Parsen der Mediendatei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 70 </td> 
   <td colname="col2"><span class="codeph"> MANIFEST_FILE_UNEXPECTEDLY_CHANGED</span> </td> 
   <td colname="col3"> Die Manifestdatei wurde unerwartet geändert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 71 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_SPLIT_TIMELINE</span> </td> 
   <td colname="col3"> Split-Vorgang auf einer Zeitleiste kann nicht durchgeführt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> Vorgang zum Löschen auf einer Zeitleiste kann nicht ausgeführt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> Das nächste Fragment wurde nicht abgerufen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> Keine Zeitschiene in einer internen Datenstruktur vorhanden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> In einer internen Datenstruktur wurde kein Listener gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_BEGINN_ERROR</span> </td> 
   <td colname="col3"> Audio kann nicht Beginn werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> In einer internen Datenstruktur ist kein Audiobecken vorhanden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> FILE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Datei kann nicht geöffnet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 79 </td> 
   <td colname="col2"><span class="codeph"> FILE_WRITE_ERROR</span> </td> 
   <td colname="col3"> In eine Datei kann nicht geschrieben werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 80 </td> 
   <td colname="col2"><span class="codeph"> FILE_READ_ERROR</span> </td> 
   <td colname="col3"> Aus einer Datei kann nicht gelesen werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 81 </td> 
   <td colname="col2"><span class="codeph"> ID3PARSE_ERROR</span> </td> 
   <td colname="col3"> Bei der Analyse der ID3-Daten ist ein Fehler aufgetreten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR  </span> </td> 
   <td colname="col3"> Das Laden des Inhalts ist aufgrund von Sicherheitsbeschränkungen fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> Die Zeitschiene ist zu kurz. Wenn es sich um einen Live-Stream handelt, kann es zu häufigen Pufferungen kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_BEGINN</span> </td> 
   <td colname="col3"> Der Stream wurde auf einen reinen Audiostream umgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> Der Stream wurde mit Video von reinem Audio auf einen Stream umgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND  </span> </td> 
   <td colname="col3"> Schlüssel kann nicht gefunden werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 88 </td> 
   <td colname="col2"><span class="codeph"> INVALID_KEY</span> </td> 
   <td colname="col3"> Der Schlüssel ist ungültig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 89 </td> 
   <td colname="col2"> <span class="codeph"> KEY_SERVER_NOT_FOUND</span> </td> 
   <td colname="col3"> Der Schlüsselserver gibt keinen Schlüssel zurück. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 90 </td> 
   <td colname="col2"> <span class="codeph"> MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</span> </td> 
   <td colname="col3"> Hauptmanifestaktualisierung kann nicht verarbeitet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Diskontinuität der nicht gemeldeten Zeit (PTS) festgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 92 </td> 
   <td colname="col2"> <span class="codeph"> UNMATCHED_AV_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Uneinheitliche Audio- und Videounterbrechung gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 93 </td> 
   <td colname="col2"><span class="codeph"> TRICKPLAY_ENDED_DUE_TO_ERROR</span> </td> 
   <td colname="col3">Beim Abspielen von Medien im Modus <i>trick play</i> ist ein Fehler aufgetreten. Der Trick Play-Modus wird beendet und der Stream wird angehalten. Rufen Sie <span class="codeph"> Play()</span> auf, um das Medium im normalen Modus abzuspielen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 95 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_AHEAD</span> </td> 
   <td colname="col3"> Der Spieler ist außerhalb des Live-Fensters und muss nach vorn suchen, um aufzuholen. </td> 
  </tr> 
 </tbody> 
</table>

