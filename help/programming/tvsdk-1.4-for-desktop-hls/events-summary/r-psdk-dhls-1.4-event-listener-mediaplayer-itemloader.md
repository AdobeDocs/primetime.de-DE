---
description: TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.
seo-description: TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.
seo-title: Loader-Ereignis
title: Loader-Ereignis
uuid: 0ad37715-14b1-457c-892f-0db0d6220f0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Loader-Ereignis{#loader-events}

TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.

Diese Ereignis bieten einen alternativen Arbeitsablauf. Sie müssen diese Schnittstelle nicht implementieren, wenn Sie eine `MediaPlayer`erstellen. Verwenden Sie dies, wenn Sie eine `MediaPlayerItemLoader`haben möchten.

Um über Ereignisse im Zusammenhang mit dem Laden einer Medienplayer-Ressource informiert zu werden, registrieren Sie Listener für die folgenden Ereignis beim `MediaPlayerItemLoader` Objekt.

| Ereignis | Bedeutung |
|---|---|
| MediaPlayerItemLoader.[abgeschlossen](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Laden der Medienressource erfolgreich abgeschlossen. |
| MediaPlayerItemLoader.[fehlgeschlagen](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Beim Laden der Medienressource ist ein Problem aufgetreten. |