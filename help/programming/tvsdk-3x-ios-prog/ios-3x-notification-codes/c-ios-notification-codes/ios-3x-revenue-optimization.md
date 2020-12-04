---
description: 'Diese Tabelle enthält detaillierte Informationen zu Umsatzoptimierungsbenachrichtigungen. '
seo-description: 'Diese Tabelle enthält detaillierte Informationen zu Umsatzoptimierungsbenachrichtigungen. '
seo-title: EINNAHMEN-Optimierungscode
title: EINNAHMEN-Optimierungscode
translation-type: tm+mt
source-git-commit: df3d60874701383325be1afdd1ec5fe036f855f8
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---


# EINNAHMEN-Optimierungscode {#revenue-optimization-code}

Diese Tabelle enthält detaillierte Informationen zu Benachrichtigungen über UMSATZOPTIMIERUNG.

## Berichte zur Umsatzoptimierung aktivieren {#enable-revenue-optimization-reporting}

Verwenden Sie zum Aktivieren dieses Berichte PTMediaPlayer api: `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>Die meisten Informationsbenachrichtigungen enthalten relevante Metadaten, z. B. die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, um anzugeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

| Code | Name | Innen-Benachrichtigung | Metadatenschlüssel | Kommentare |
|---|---|---|---|---|
| 401001 | REVENUE_OPTIMIZATION_BERICHTE | Keines | Die folgende Tabelle enthält Metadatenschlüssel, die auf verschiedenen Ereignissen basieren. | Keines |

| Ereignis-Details | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_** STARTDispatched in TVSDK, wenn MediaPlayer::replaceCurrentResource aufgerufen wird. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, Ereignis, adSignalingMode, resourceUrl, creativeRepackageFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adRequestTimeout, delayAdLoading, resourceType, creativeRepackageEncryption abled, mediaId, clientId |
| **CONTENT_PLAYBACK_** STARTDispatched in TVSDK, wenn Inhalt den vorbereiteten Status erreicht hat und zur Wiedergabe bereit ist. Dieses Ereignis wird nicht bei jedem Manifest-Upload ausgelöst - es wird nur beim ersten Laden ausgelöst. | clientTimestamp, contentURL, contentType, Ereignis, isLive, clientID |
| **AD_OPPORTUNITY_** GENERATEDDispatched in TVSDK, wenn eine Gelegenheit generiert wird. | clientTimestamp, Ereignis, Id, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_** STARTDispatched in TVSDK, wenn eine Gelegenheit zu lösen beginnt. | clientTimestamp, Ereignis, Id, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_** FAILEDDispatched in TVSDK, wenn ein Anzeigenauflöser MediaPlayerClient::notificationFailed() aufruft. Daten ausfüllen | possibleId, notificationAD |
| **AD_RESOURCE_** LOADDispatched, wenn eine beliebige Anzeigenressource von einer URL abgerufen wird. responseStartTime:Unix-Zeitstempel für den Zeitpunkt, zu dem die Anforderung zum ersten Mal gestartet wurde. responseTotalTime: Gesamtdauer (in Sekunden), die es dauerte, bis eine Antwort geladen wurde. responseStatus: Der Statuscode, der beim Abrufen der Ressource aufgetreten ist. status:&quot;error&quot;oder &quot;success&quot;referrerAdId:Die verweisende Anzeigen-ID, die das Abrufen dieser Ressource angefordert hat (sofern vorhanden). referrerUrl: Die verweisende URL, die das Abrufen dieser Ressource angefordert hat. errorMessage: Wenn der Status &quot;error&quot;lautet, wird der Grund für den Fehler hier angegeben. | ungschancenId, resourceType, responseTotalTime, responseStatus, responseStartTime, Status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_** CRSDispatched in TVSDK, wenn ein CRS auf ein Asset angewendet wird, sowie die Antwort für m3u8. resourceType:always &quot;crs&quot;. responseStartTime:Unix-Zeitstempel für den Zeitpunkt, zu dem die Anforderung zum ersten Mal gestartet wurde. responseTotalTime: Gesamtdauer (in Sekunden), die es dauerte, bis eine Antwort geladen wurde. responseStatus: Der Statuscode, der beim Abrufen der Ressource aufgetreten ist. status:&quot;error&quot;oder &quot;success&quot;. errorMessage: Wenn der Status &quot;error&quot;lautet, wird der Grund für den Fehler hier angegeben. mediaFileUrl: Die URL der ursprünglichen Mediendatei, die ausgewählt wurde. mediaFileBitrate: Die Bitrate der ausgewählten Mediendatei. mediaFileMimeType: Der Mime-Typ der ausgewählten Mediendatei. url: Die endgültige Asset-URL. | ungschancenId, resourceType, responseTotalTime, responseStatus, responseStartTime, Status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_** PLACEDispatched in TVSDK, nachdem ein adBreak auf der Zeitleiste platziert wurde. Dieses Ereignis tritt einmal pro Werbeunterbrechung auf. providedTime: Der Zeitpunkt, zu dem die Werbeunterbrechung platziert werden soll. ISTTime: Der Zeitpunkt, zu dem die Werbeunterbrechung tatsächlich platziert wurde. providedDuration: Die Dauer der Werbeunterbrechung, die zum Einfügen angefordert wurde. Bei Live-Inhalten wäre dies die Cue-Dauer. Für VOD-Inhalte wäre dies normalerweise -1. effectiveDuration: Die tatsächliche Dauer der Werbeunterbrechung. Berechnet als die Gesamtdauer aller Anzeigen, definiert durch ihre jeweilige Segmentdauer, die in der ursprünglichen Stream-Zeitleiste hinzugefügt oder ersetzt wurde. providedAds: Die Anzahl der Anzeigen in der vorgeschlagenen Werbeunterbrechung. totalAds: Die Anzahl der Anzeigen, die erfolgreich platziert wurden. Anzeigen...n:Die erfolgreich eingefügten Anzeigen werden hier eingefügt. Die gesamten Anzeigenmanifestinformationen können von AD_OPPORTUNITY_RESOLVE_PROCESS abgerufen werden. | availabilityId, status, errorMessage, providedTime, providedDuration, ISTTime, ISTDuration, providedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_** STARTDispatched in TVSDK, nachdem eine Anzeige mit der Wiedergabe beginnt. | clientTimestamp, Ereignis, id, url, duration, type, offerId, clientId |
| **AD_PLAYBACK_** COMPLETEDispatched in TVSDK, nachdem eine Anzeige die Wiedergabe abgeschlossen hat. | clientTimestamp, Ereignis, id, url, duration, type, offerId, clientId |
| **ADBREAK_PLAYBACK_** STARTDispatched in TVSDK, wenn ein Adbreak-Beginn die Wiedergabe durchführt. | clientTimestamp, Ereignis, Id, duration, time, clientId |
| **ADBREAK_PLAYBACK_** COMPLETEDispatched in TVSDK, wenn eine Werbeunterbrechung die Wiedergabe abgeschlossen hat. | clientTimestamp, Ereignis, Id, clientId |
| **CONTENT_PLAYBACK_** COMPLETEDispatched in TVSDK, wenn ein Inhalt abgeschlossen ist. Dies kann vorkommen, wenn der Stream ersetzt wird, der Player einen Fehlerstatus eingibt, der Player zurückgesetzt wird oder der Inhalt tatsächlich abgeschlossen wird. Dieses Ereignis ist zur Verfolgung einer sessionId erforderlich. | clientTimestamp, Ereignis, clientId, url, status, errorMessage |
| **AD_PLAYBACK_** ERRORDispatched in TVSDK, wenn eine Anzeige einen Fehler bei der Wiedergabe aufweist (Variantenstream-Fehler). | ereignis, error, Timestamp, manifestUrl, time, Id, url |
