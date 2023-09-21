---
description: TVSDK sendet Servicequalitätsereignisse (QoS), um Ihre Anwendung über Ereignisse zu informieren, die die Berechnung von QoS-Statistiken beeinflussen könnten, z. B. Pufferung oder Suche.
title: QoS-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# QoS-Ereignisse{#qos-events}

TVSDK sendet Servicequalitätsereignisse (QoS), um Ihre Anwendung über Ereignisse zu informieren, die die Berechnung von QoS-Statistiken beeinflussen könnten, z. B. Pufferung oder Suche.

Um über alle QoS-bezogenen Ereignisse informiert zu werden, registrieren Sie eine Implementierung von `MediaPlayer.QOSEventListener` einschließlich der folgenden Rückrufe:

| Ereignis | Bedeutung |
|---|---|
| [onBufferComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferComplete()) | Die Pufferung ist abgeschlossen. |
| [onBufferStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferStart()) | Die Pufferung wurde gestartet. |
| [onLoadInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onLoadInfo(com.adobe.mediacore.qos.LoadInfo))(loadInfo) | Ein Fragment wurde erfolgreich heruntergeladen. |
| [onOperationFailed](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html)(MediaPlayerNotification. [Warnung](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) warning) | Ein wiederherstellbarer Fehler ist aufgetreten. |
| [onSeekComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekComplete(long))(long AdjustedTime) | Die Suche ist abgeschlossen. |
| [onSeekStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekStart()) | Die Suche fängt an. |
