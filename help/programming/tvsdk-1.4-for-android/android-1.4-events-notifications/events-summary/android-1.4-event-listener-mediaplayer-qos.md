---
description: TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung von Servicestatistiken wie Pufferung oder Suche beeinflussen könnten.
seo-description: TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung von Servicestatistiken wie Pufferung oder Suche beeinflussen könnten.
seo-title: QoS-Ereignis
title: QoS-Ereignis
uuid: 27f60cd3-d3fc-4ea3-81df-96d0fe9f7068
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# QoS-Ereignis{#qos-events}

TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung von Servicestatistiken wie Pufferung oder Suche beeinflussen könnten.

Um über alle QoS-bezogenen Ereignis informiert zu werden, registrieren Sie eine Implementierung von `MediaPlayer.QOSEventListener` einschließlich der folgenden Rückrufe:

| Ereignis | Bedeutung |
|---|---|
| [onBufferComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferComplete()) | Die Pufferung ist abgeschlossen. |
| [onBufferStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferStart()) | Die Pufferung wurde gestartet. |
| [onLoadInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onLoadInfo(com.adobe.mediacore.qos.LoadInfo))(loadInfo) | Ein Fragment wurde erfolgreich heruntergeladen. |
| [onOperationFailure](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html)(MediaPlayerNotification). [Warnung ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) bei Warnungen) | Ein wiederherstellbarer Fehler ist aufgetreten. |
| [onSeekComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekComplete(long))(long adjustierteTime) | Die Suche ist abgeschlossen. |
| [onSeekStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekStart()) | Die Suche fängt an. |