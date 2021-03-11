---
description: TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.
title: Loader-Ereignis
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Loader-Ereignis{#loader-events}

TVSDK sendet Medienplayer-Element-Ereignis als Reaktion auf das Laden eines Medienelements.

Diese Ereignis bieten einen alternativen Arbeitsablauf. Sie müssen diese Schnittstelle nicht implementieren, wenn Sie ein `MediaPlayer` erstellen. Verwenden Sie dies, wenn Sie ein `MediaPlayerItemLoader` haben möchten.

Um über Ereignisse im Zusammenhang mit dem Laden einer Medienplayer-Ressource informiert zu werden, registrieren Sie Listener für die folgenden Ereignis mit dem `MediaPlayerItemLoader`-Objekt.

| Ereignis | Bedeutung |
|---|---|
| MediaPlayerItemLoader.[abgeschlossen](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Laden der Medienressource erfolgreich abgeschlossen. |
| MediaPlayerItemLoader.[fehlgeschlagen](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Beim Laden der Medienressource ist ein Problem aufgetreten. |