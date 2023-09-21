---
description: TVSDK sendet Medienplayer-Elementereignisse als Reaktion auf das Laden eines Medienelements.
title: Ladeereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Ladeereignisse{#loader-events}

TVSDK sendet Medienplayer-Elementereignisse als Reaktion auf das Laden eines Medienelements.

Diese Ereignisse bieten einen alternativen Workflow. Sie müssen diese Schnittstelle beim Erstellen eines MediaPlayer nicht implementieren. Verwenden Sie dies, wenn Sie eine `MediaPlayerItemLoader`.

Um über Ereignisse im Zusammenhang mit dem Laden einer Medienplayer-Ressource informiert zu werden, registrieren Sie eine Implementierung von `MediaPlayerItemLoader.LoaderListener` einschließlich der folgenden Ereignisse.

| Ereignis | Bedeutung |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | Das Laden der Medienressource wurde erfolgreich abgeschlossen. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Beim Laden der Medienressource ist ein Problem aufgetreten. |

>[!NOTE]
>
>Siehe auch `onLoadInfo (loadInfo)` unter QoS-Ereignisse.
