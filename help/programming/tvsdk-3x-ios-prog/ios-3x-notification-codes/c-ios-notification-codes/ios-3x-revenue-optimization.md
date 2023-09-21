---
description: Diese Tabelle enthält detaillierte Informationen zu Benachrichtigungen zur Umsatzoptimierung.
title: EINNAHMEN-Optimierungscode
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# EINNAHMEN-Optimierungscode {#revenue-optimization-code}

Diese Tabelle enthält detaillierte Informationen zu Benachrichtigungen zur UMSATZOPTIMIERUNG.

## Berichte zur Umsatzoptimierung aktivieren {#enable-revenue-optimization-reporting}

Verwenden Sie die PTMediaPlayer-API, um diese Berichterstellung zu aktivieren: `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>Die meisten Informationsbenachrichtigungen enthalten relevante Metadaten, beispielsweise die URL der Ressource, die nicht heruntergeladen werden konnte. Einige Benachrichtigungen enthalten Metadaten, die angeben, ob das Problem im Hauptvideoinhalt, im alternativen Audioinhalt oder in einer Anzeige aufgetreten ist.

| Code | Name | Innen-Benachrichtigung | Metadatenschlüssel | Kommentare |
|---|---|---|---|---|
| 401001 | REVENUE_OPTIMIZATION_REPORTING | Keines | Die folgende Tabelle enthält Metadatenschlüssel, die auf verschiedenen Ereignissen basieren. | Keines |

| Ereignisdetails | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_START** Wird in TVSDK ausgelöst, wenn MediaPlayer::replaceCurrentResource aufgerufen wird. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, event, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adRequestTimeout, delayAdLoading, resourceType, creativeRepackagingEnabled, mediaId, clientId |
| **CONTENT_PLAYBACK_START** Wird in TVSDK gesendet, wenn der Inhalt in den vorbereiteten Status versetzt wurde und zur Wiedergabe bereit ist. Dieses Ereignis wird nicht bei jedem Manifest-Upload gesendet - wird nur beim ersten Laden gesendet. | clientTimestamp, contentURL, contentType, event, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** Wird in TVSDK gesendet, wenn eine Chance generiert wird. | clientTimestamp, event, OpportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_START** Wird in TVSDK gesendet, wenn eine Gelegenheit aufgelöst wird. | clientTimestamp, event, OpportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** Wird in TVSDK ausgelöst, wenn ein Anzeigenauflöser MediaPlayerClient::notifyFailed() aufruft. Daten ausfüllen | OpportunityId, notificationAD |
| **AD_RESOURCE_LOAD** Wird ausgelöst, wenn eine Anzeigenressource von einer URL abgerufen wird. responseStartTime:Unix-Zeitstempel für den Zeitpunkt, zu dem die Anfrage zum ersten Mal gestartet wurde. responseTotalTime: Gesamtdauer (in Sekunden), die für das Laden einer Antwort benötigt wurde. responseStatus:Der beim Abrufen der Ressource aufgetretene Statuscode. status:&quot;error&quot;oder &quot;success&quot; referrerAdId: Die Referrer-Anzeigen-ID, die den Abruf dieser Ressource angefordert hat (sofern vorhanden). referrerUrl: Die verweisende URL, die den Abruf dieser Ressource angefordert hat. errorMessage: Wenn der Status &quot;error&quot;lautet, wird der Grund für den Fehler hier angegeben. | unityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_CRS** Wird in TVSDK gesendet, wenn ein CRS auf ein Asset angewendet wird, sowie die Antwort für m3u8. resourceType:always &quot;crs&quot;. responseStartTime:Unix-Zeitstempel für den Zeitpunkt, zu dem die Anfrage zum ersten Mal gestartet wurde. responseTotalTime: Gesamtdauer (in Sekunden), die für das Laden einer Antwort benötigt wurde. responseStatus:Der beim Abrufen der Ressource aufgetretene Statuscode. status:&quot;error&quot;oder &quot;success&quot;. errorMessage: Wenn der Status &quot;error&quot;lautet, wird der Grund für den Fehler hier angegeben. mediaFileUrl: Die ursprüngliche Mediendatei-URL, die ausgewählt wurde. mediaFileBitrate: Die Bitrate der ausgewählten Mediendatei. mediaFileMimeType: Der MIME-Typ der ausgewählten Mediendatei. url: Die endgültige Asset-URL. | unityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** Wird in TVSDK gesendet, nachdem eine adBreak auf der Timeline platziert wurde. Dieses Ereignis tritt einmal für jede Werbeunterbrechung auf. preparedTime: Der Zeitpunkt, zu dem die Werbeunterbrechung platziert werden soll. ISTTime: Die Zeit, in der die Werbeunterbrechung tatsächlich platziert wurde. recommendedDuration: Die Dauer der Werbeunterbrechung, die zum Einfügen angefordert wurde. Bei Live-Inhalten wäre dies die Cue-Point-Dauer. Für VOD-Inhalte wäre dies normalerweise -1. effectiveDuration: Die tatsächliche Dauer der eingefügten Werbeunterbrechung. Berechnet als Gesamtdauer aller Anzeigen, definiert durch ihre jeweilige Segmentdauer, die in der ursprünglichen Stream-Timeline hinzugefügt oder ersetzt wurden. Anzeige: Die Anzahl der Anzeigen in der vorgeschlagenen Werbeunterbrechung. totalAds: Die Anzahl der Anzeigen, die erfolgreich platziert wurden. ads...n: Die erfolgreich eingefügten Anzeigen werden hier eingefügt. Gesamte Anzeigenmanifestinformationen können von AD_OPPORTUNITY_RESOLVE_PROCESS abgerufen werden | OpportunityId, status, errorMessage, preparedTime, preparedDuration, effectiveTime, effectiveAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_START** Wird in TVSDK gesendet, nachdem die Wiedergabe einer Anzeige beginnt. | clientTimestamp, event, id, url, duration, type, OpportunityId, clientId |
| **AD_PLAYBACK_COMPLETE** Wird in TVSDK gesendet, nachdem die Wiedergabe einer Anzeige abgeschlossen ist. | clientTimestamp, event, id, url, duration, type, OpportunityId, clientId |
| **ADBREAK_PLAYBACK_START** Wird in TVSDK gesendet, wenn eine Werbeunterbrechung die Wiedergabe startet. | clientTimestamp, event, OpportunityId, duration, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** Wird in TVSDK gesendet, wenn die Wiedergabe einer Werbeunterbrechung abgeschlossen ist. | clientTimestamp, event, OpportunityId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** Wird in TVSDK gesendet, wenn ein Inhalt abgeschlossen ist. Dies kann vorkommen, wenn der Stream ersetzt wird, der Player einen Fehlerstatus eingibt, der Player zurückgesetzt wird oder der Inhalt tatsächlich abgeschlossen ist. Dieses Ereignis ist erforderlich, um eine sessionId zu verfolgen. | clientTimestamp, event, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** Wird in TVSDK gesendet, wenn die Wiedergabe einer Anzeige einen Fehler aufweist (Variantenstream-Fehler). | event, error, Timestamp, manifestUrl, time, unityId, url |
