---
description: TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung von Servicestatistiken wie Pufferung oder Suche beeinflussen könnten.
seo-description: TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung von Servicestatistiken wie Pufferung oder Suche beeinflussen könnten.
seo-title: QoS-Ereignis
title: QoS-Ereignis
uuid: fd657cf0-c6d4-4e9a-b212-7d09d483cae9
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '219'
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
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK änderte die Suchposition aufgrund der aktuellen Werberichtlinien. |

