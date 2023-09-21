---
description: TVSDK sendet Servicequalitätsereignisse (QoS), um Ihre Anwendung über Ereignisse zu informieren, die die Berechnung von QoS-Statistiken beeinflussen könnten, z. B. Pufferung oder Suche.
title: QoS-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# QoS-Ereignisse{#qos-events}

TVSDK sendet Servicequalitätsereignisse (QoS), um Ihre Anwendung über Ereignisse zu informieren, die die Berechnung von QoS-Statistiken beeinflussen könnten, z. B. Pufferung oder Suche.

Um über alle QoS-bezogenen Ereignisse informiert zu werden, registrieren Sie Ereignis-Listener bei der `MediaPlayer` -Objekt für die folgenden Ereignisse:

| Ereignis | Bedeutung |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | Die Pufferung ist abgeschlossen. |
| BufferEvent.[PUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | Die Pufferung wurde gestartet. |
| SeekEvent.[SEEK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | Die Suche ist abgeschlossen. |
| SeekEvent.[SEEK_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | Die Suche fängt an. |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK hat die Suchposition aufgrund der aktuellen Werberichtlinien geändert. |
