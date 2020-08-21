---
description: 'Diese Tabelle enthält detaillierte Informationen zu Umsatzoptimierungsbenachrichtigungen. '
seo-description: 'Diese Tabelle enthält detaillierte Informationen zu Umsatzoptimierungsbenachrichtigungen. '
seo-title: EINNAHMEN-Optimierungscode
title: EINNAHMEN-Optimierungscode
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# EINNAHMEN-Optimierungscode {#revenue-optimization-code}

Diese Tabelle enthält detaillierte Informationen zu Benachrichtigungen über UMSATZOPTIMIERUNG.

## Berichte zur Umsatzoptimierung aktivieren {#enable-revenue-optimization-reporting}

Verwenden Sie zum Aktivieren dieses Berichte PTMediaPlayer api: `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>Die meisten Informationsbenachrichtigungen enthalten relevante Metadaten, z. B. die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, um anzugeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

|Code |Name |Innen-Benachrichtigung |Metadatenschlüssel |Anmerkungen |
|—|—|—|—|—|—|
| 401001 | REVENUE_OPTIMIZATION_BERICHTE | Keine | Metadatenschlüssel auf Basis verschiedener Ereignis finden Sie in der folgenden Tabelle. | Keine |

| Ereignis-Details | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_BEGINN** wird in TVSDK ausgelöst, wenn MediaPlayer::replaceCurrentResource aufgerufen wird. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, Ereignis, adSignalingMode, resourceUrl, creativeRepackageFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adRequestTimeout, delayAdLoading, resourceType, creativeRepackageEncryption abled, mediaId, clientId |
| **CONTENT_PLAYBACK_BEGINN** wird in TVSDK abgesetzt, wenn der Inhalt in den vorbereiteten Status gelangt ist und zur Wiedergabe bereit ist. Dieses Ereignis wird nicht bei jedem Manifest-Upload ausgelöst - es wird nur beim ersten Laden ausgelöst. | clientTimestamp, contentURL, contentType, Ereignis, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** Dispatched in TVSDK, wenn eine Gelegenheit generiert wird. | clientTimestamp, Ereignis, Id, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_BEGINN** wird in TVSDK abgesetzt, wenn eine Gelegenheit zu lösen beginnt. | clientTimestamp, Ereignis, Id, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** Dispatched in TVSDK, wenn ein Anzeigenauflöser MediaPlayerClient::notificationFailed() aufruft. Daten ausfüllen | possibleId, notificationAD |
| **AD_RESOURCE_LOAD** Wird ausgelöst, wenn eine beliebige Anzeigenressource von einer URL abgerufen wird. responseStartTime:Unix-Zeitstempel für den Zeitpunkt, zu dem die Anforderung zum ersten Mal gestartet wurde. responseTotalTime: Gesamtdauer (in Sekunden), die es dauerte, bis eine Antwort geladen wurde. responseStatus: Der Statuscode, der beim Abrufen der Ressource aufgetreten ist. status:&quot;error&quot;oder &quot;success&quot;referrerAdId:Die verweisende Anzeigen-ID, die das Abrufen dieser Ressource angefordert hat (sofern vorhanden). referrerUrl: Die verweisende URL, die das Abrufen dieser Ressource angefordert hat. errorMessage: Wenn der Status &quot;error&quot;lautet, wird der Grund für den Fehler hier angegeben. | ungschancenId, resourceType, responseTotalTime, responseStatus, responseStartTime, Status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_CRS** Wird in TVSDK ausgelöst, wenn ein CRS auf ein Asset angewendet wird, sowie die Antwort für m3u8. resourceType:always &quot;crs&quot;. responseStartTime:Unix-Zeitstempel für den Zeitpunkt, zu dem die Anforderung zum ersten Mal gestartet wurde. responseTotalTime: Gesamtdauer (in Sekunden), die es dauerte, bis eine Antwort geladen wurde. responseStatus: Der Statuscode, der beim Abrufen der Ressource aufgetreten ist. status:&quot;error&quot;oder &quot;success&quot;. errorMessage: Wenn der Status &quot;error&quot;lautet, wird der Grund für den Fehler hier angegeben. mediaFileUrl: Die URL der ursprünglichen Mediendatei, die ausgewählt wurde. mediaFileBitrate: Die Bitrate der ausgewählten Mediendatei. mediaFileMimeType: Der Mime-Typ der ausgewählten Mediendatei. url: Die endgültige Asset-URL. | ungschancenId, resourceType, responseTotalTime, responseStatus, responseStartTime, Status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** wird in TVSDK abgesetzt, nachdem ein adBreak auf der Zeitleiste platziert wurde. Dieses Ereignis tritt einmal pro Werbeunterbrechung auf. providedTime: Der Zeitpunkt, zu dem die Werbeunterbrechung platziert werden soll. ISTTime: Der Zeitpunkt, zu dem die Werbeunterbrechung tatsächlich platziert wurde. providedDuration: Die Dauer der Werbeunterbrechung, die zum Einfügen angefordert wurde. Bei Live-Inhalten wäre dies die Cue-Dauer. Für VOD-Inhalte wäre dies normalerweise -1. effectiveDuration: Die tatsächliche Dauer der Werbeunterbrechung. Berechnet als die Gesamtdauer aller Anzeigen, definiert durch ihre jeweilige Segmentdauer, die in der ursprünglichen Stream-Zeitleiste hinzugefügt oder ersetzt wurde. providedAds: Die Anzahl der Anzeigen in der vorgeschlagenen Werbeunterbrechung. totalAds: Die Anzahl der Anzeigen, die erfolgreich platziert wurden. Anzeigen...n:Die erfolgreich eingefügten Anzeigen werden hier eingefügt. Die gesamten Anzeigenmanifestinformationen können von AD_OPPORTUNITY_RESOLVE_PROCESS abgerufen werden. | availabilityId, status, errorMessage, providedTime, providedDuration, ISTTime, ISTDuration, providedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_BEGINN** wird in TVSDK ausgelöst, nachdem die Wiedergabe einer Anzeige begonnen hat. | clientTimestamp, Ereignis, id, url, duration, type, offerId, clientId |
| **AD_PLAYBACK_COMPLETE** wird in TVSDK nach Abschluss der Wiedergabe einer Anzeige ausgelöst. | clientTimestamp, Ereignis, id, url, duration, type, offerId, clientId |
| **ADBREAK_PLAYBACK_BEGINN** wird in TVSDK ausgelöst, wenn ein Adbreak-Beginn die Wiedergabe durchführt. | clientTimestamp, Ereignis, Id, duration, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** wird in TVSDK ausgelöst, wenn die Wiedergabe eines Werbeunterbrechers abgeschlossen ist. | clientTimestamp, Ereignis, Id, clientId |
| **CONTENT_PLAYBACK_COMPLETE** Wird in TVSDK ausgelöst, wenn ein Inhalt abgeschlossen ist. Dies kann vorkommen, wenn der Stream ersetzt wird, der Player einen Fehlerstatus eingibt, der Player zurückgesetzt wird oder der Inhalt tatsächlich abgeschlossen ist. Dieses Ereignis ist zur Verfolgung einer sessionId erforderlich. | clientTimestamp, Ereignis, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** Wird in TVSDK ausgelöst, wenn eine Anzeige einen Fehler bei der Wiedergabe aufweist (Variantenstream-Fehler). | ereignis, error, Timestamp, manifestUrl, time, Id, url |