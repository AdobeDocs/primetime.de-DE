---
description: TVSDK löst Ereignis zur Anzeigenwiedergabe aus, die auf anzeigenbezogene Vorgänge reagieren, z. B. wenn eine Anzeige Beginn wird.
seo-description: TVSDK löst Ereignis zur Anzeigenwiedergabe aus, die auf anzeigenbezogene Vorgänge reagieren, z. B. wenn eine Anzeige Beginn wird.
seo-title: Ereignisse zur Anzeigenwiedergabe
title: Ereignisse zur Anzeigenwiedergabe
uuid: 63138237-2315-45ff-914d-369da18fdff7
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# Ereignisse für die Anzeigenwiedergabe {#ad-playback-events}

TVSDK löst Ereignis zur Anzeigenwiedergabe aus, die auf anzeigenbezogene Vorgänge reagieren, z. B. wenn eine Anzeige Beginn wird.

Um über alle mit der Anzeigenwiedergabe zusammenhängenden Ereignis benachrichtigt zu werden, registrieren Sie Listener für die folgenden Ereignis beim `MediaPlayer`-Objekt.

>[!TIP]
>
>Wenn Anzeigen in das Medium eingefügt oder daraus entfernt werden, löst TVSDK das play-Ereignis TimelineEvent aus.[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| Ereignis | Bedeutung |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | Eine Werbeunterbrechung wurde vollständig abgespielt. |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | Während der Wiedergabe wurde eine Werbeunterbrechung übersprungen. |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | Eine Werbeunterbrechung wurde gestartet. |
| AdClickEvent.[AD_CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | Der Benutzer hat auf die Anzeige geklickt. Stellt Informationen für Ihre Anwendung über die Anzeige bereit, auf die der Benutzer geklickt hat, nachdem Ihre Anwendung `notifyClick` auf `MediaPlayerView` aufgerufen hat. |
| AdPlaybackEvent.[ANZEIGE_ABGESCHLOSSEN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | Eine Anzeige wurde vollständig abgespielt. |
| AdPlaybackEvent.[AD_PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | Die Anzeigenwiedergabe ist vorangekommen. Wird mehrmals während der Wiedergabe einer Anzeige ausgelöst. |
| AdPlaybackEvent.[AD_SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Eine Suche erfolgte über Anzeigengrenzen hinweg oder innerhalb einer Anzeige. |
| AdPlaybackEvent.[ANZEIGE_STARTET](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Eine Anzeige wurde gestartet. |