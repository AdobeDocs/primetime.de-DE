---
description: TVSDK versendet Anzeigenwiedergabe-Ereignisse als Reaktion auf anzeigenbezogene Vorgänge, z. B. wenn die Wiedergabe einer Anzeige beginnt.
title: Anzeigenwiedergabeereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Anzeigenwiedergabeereignisse {#ad-playback-events}

TVSDK versendet Anzeigenwiedergabe-Ereignisse als Reaktion auf anzeigenbezogene Vorgänge, z. B. wenn die Wiedergabe einer Anzeige beginnt.

Um über alle Ereignisse im Zusammenhang mit der Anzeigenwiedergabe informiert zu werden, registrieren Sie Listener bei der `MediaPlayer` -Objekt für die folgenden Ereignisse.

>[!TIP]
>
>Wenn Anzeigen in Medien eingefügt oder aus diesen entfernt werden, sendet TVSDK das Wiedergabeereignis TimelineEvent.[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| Ereignis | Bedeutung |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | Eine Werbeunterbrechung wurde vollständig wiedergegeben. |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | Während der Wiedergabe wurde eine Werbeunterbrechung übersprungen. |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | Eine Werbeunterbrechung hat begonnen. |
| AdClickEvent.[AD_CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | Der Benutzer hat auf die Anzeige geklickt. Stellt Informationen für Ihre Anwendung über die Anzeige bereit, auf die der Benutzer als Reaktion auf den Aufruf Ihrer Anwendung geklickt hat `notifyClick` auf `MediaPlayerView`. |
| AdPlaybackEvent.[AD_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | Eine Anzeige wurde vollständig wiedergegeben. |
| AdPlaybackEvent.[AD_PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | Die Anzeigenwiedergabe wurde fortgesetzt. Wird mehrmals bei der Wiedergabe einer Anzeige ausgelöst. |
| AdPlaybackEvent.[AD_SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Über Anzeigengrenzen oder innerhalb einer Anzeige hinweg wurde eine Suche durchgeführt. |
| AdPlaybackEvent.[AD_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Eine Anzeige wurde gestartet. |
