---
description: TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung von Servicestatistiken wie Pufferung oder Suche beeinflussen könnten.
title: QoS-Ereignis
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# QoS-Ereignis{#qos-events}

TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung von Servicestatistiken wie Pufferung oder Suche beeinflussen könnten.

Um über alle QoS-bezogenen Ereignis benachrichtigt zu werden, registrieren Sie Ereignis-Listener mit dem `MediaPlayer`-Objekt für die folgenden Ereignis:

| Ereignis | Bedeutung |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | Die Pufferung ist abgeschlossen. |
| BufferEvent.[BUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | Die Pufferung wurde gestartet. |
| SeekEvent.[SEEK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | Die Suche ist abgeschlossen. |
| SeekEvent.[SEEK_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | Die Suche fängt an. |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK änderte die Suchposition aufgrund der aktuellen Werbepolitik. |

