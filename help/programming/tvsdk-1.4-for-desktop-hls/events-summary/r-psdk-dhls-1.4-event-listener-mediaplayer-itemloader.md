---
description: TVSDK sendet Medienplayer-Elementereignisse als Reaktion auf das Laden eines Medienelements.
title: Ladeereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Ladeereignisse{#loader-events}

TVSDK sendet Medienplayer-Elementereignisse als Reaktion auf das Laden eines Medienelements.

Diese Ereignisse bieten einen alternativen Workflow. Sie müssen diese Schnittstelle beim Erstellen einer `MediaPlayer`. Verwenden Sie dies, wenn Sie eine `MediaPlayerItemLoader`.

Um über Ereignisse im Zusammenhang mit dem Laden einer Medienplayer-Ressource informiert zu werden, registrieren Sie Listener für die folgenden Ereignisse bei der `MediaPlayerItemLoader` -Objekt.

| Ereignis | Bedeutung |
|---|---|
| MediaPlayerItemLoader.[completed](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Das Laden der Medienressource wurde erfolgreich abgeschlossen. |
| MediaPlayerItemLoader.[failed](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Beim Laden der Medienressource ist ein Problem aufgetreten. |
