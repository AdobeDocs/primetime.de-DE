---
description: TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.
seo-description: TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.
seo-title: Loader-Ereignis
title: Loader-Ereignis
uuid: 1b401ff5-4313-4c64-8be9-99bdeb58ba2a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Loader-Ereignis{#loader-events}

TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.

Diese Ereignis bieten einen alternativen Arbeitsablauf. Sie müssen diese Schnittstelle beim Erstellen eines MediaPlayer nicht implementieren. Verwenden Sie dies, wenn Sie eine `MediaPlayerItemLoader`haben möchten.

Um über Ereignisse im Zusammenhang mit dem Laden einer Medienplayer-Ressource informiert zu werden, registrieren Sie eine Implementierung von `MediaPlayerItemLoader.LoaderListener` einschließlich der folgenden Ereignis.

| Ereignis | Bedeutung |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | Laden der Medienressource erfolgreich abgeschlossen. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Beim Laden der Medienressource ist ein Problem aufgetreten. |

>[!NOTE]
>
>Siehe auch `onLoadInfo (loadInfo)` unter QoS-Ereignisse.

