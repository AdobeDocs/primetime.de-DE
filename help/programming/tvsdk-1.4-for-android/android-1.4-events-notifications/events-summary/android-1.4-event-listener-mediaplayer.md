---
description: TVSDK löst Ereignis zur Anzeigenwiedergabe aus, die auf anzeigenbezogene Vorgänge reagieren, z. B. wenn eine Anzeige Beginn wird.
seo-description: TVSDK löst Ereignis zur Anzeigenwiedergabe aus, die auf anzeigenbezogene Vorgänge reagieren, z. B. wenn eine Anzeige Beginn wird.
seo-title: Ereignisse zur Anzeigenwiedergabe
title: Ereignisse zur Anzeigenwiedergabe
uuid: dd6991ae-3e33-4d92-92e9-26b1086a555a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---


# Ereignisse zur Anzeigenwiedergabe{#ad-playback-events}

TVSDK löst Ereignis zur Anzeigenwiedergabe aus, die auf anzeigenbezogene Vorgänge reagieren, z. B. wenn eine Anzeige Beginn wird.

Um über alle mit der Anzeigenwiedergabe zusammenhängenden Ereignis informiert zu werden, registrieren Sie eine Implementierung von `MediaPlayer.AdPlaybackEventListener` einschließlich der folgenden Rückrufe.

>[!TIP]
>
>Wenn Anzeigen in Medien eingefügt oder aus diesen entfernt werden, löst TVSDK das Ereignis für die Wiedergabe [onTimelineUpdated](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated()) aus.

| Ereignis | Bedeutung |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Eine Werbeunterbrechung wurde vollständig abgespielt. |
| onAdBreakSkipping | Während der Wiedergabe wurde eine Werbeunterbrechung übersprungen. |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Eine Werbeunterbrechung wurde gestartet. |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, Ad AdAd, AdClick adClick) | Der Benutzer hat auf die Anzeige geklickt. Stellt Informationen für Ihre Anwendung über die Anzeige bereit, auf die der Benutzer geklickt hat, nachdem Ihre Anwendung `notifyClick` auf `MediaPlayerView` aufgerufen hat. |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak, Ad ad ad) | Eine Anzeige wurde vollständig abgespielt. |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int)) (AdBreak adBreak, Ad Ad Ad Ad, int Prozentwert) | Die Anzeigenwiedergabe ist vorangekommen. Wird mehrmals während der Wiedergabe einer Anzeige ausgelöst. |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak adBreak, Ad ad) | Eine Anzeige wurde gestartet. |