---
description: TVSDK versendet Anzeigenwiedergabe-Ereignisse als Reaktion auf anzeigenbezogene Vorgänge, z. B. wenn die Wiedergabe einer Anzeige beginnt.
title: Anzeigenwiedergabeereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Anzeigenwiedergabeereignisse{#ad-playback-events}

TVSDK versendet Anzeigenwiedergabe-Ereignisse als Reaktion auf anzeigenbezogene Vorgänge, z. B. wenn die Wiedergabe einer Anzeige beginnt.

Um über alle Ereignisse im Zusammenhang mit der Anzeigenwiedergabe informiert zu werden, registrieren Sie eine Implementierung von `MediaPlayer.AdPlaybackEventListener` einschließlich der folgenden Rückrufe.

>[!TIP]
>
>Wenn Anzeigen in Medien eingefügt oder aus diesen entfernt werden, sendet TVSDK das Wiedergabeereignis [onTimelineUpdated](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated()).

| Ereignis | Bedeutung |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Eine Werbeunterbrechung wurde vollständig wiedergegeben. |
| onAdBreakSkipped | Während der Wiedergabe wurde eine Werbeunterbrechung übersprungen. |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Eine Werbeunterbrechung hat begonnen. |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, Ad-Anzeige, AdClick adClick) | Der Benutzer hat auf die Anzeige geklickt. Stellt Informationen für Ihre Anwendung über die Anzeige bereit, auf die der Benutzer als Reaktion auf den Aufruf Ihrer Anwendung geklickt hat `notifyClick` auf `MediaPlayerView`. |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak, Ad-Anzeige) | Eine Anzeige wurde vollständig wiedergegeben. |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int)) (AdBreak adBreak, Ad-Anzeige, int-Prozent) | Die Anzeigenwiedergabe wurde fortgesetzt. Wird mehrmals bei der Wiedergabe einer Anzeige ausgelöst. |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak adBreak, Ad-Anzeige) | Eine Anzeige wurde gestartet. |
