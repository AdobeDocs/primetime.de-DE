---
description: TVSDK sendet Adserving-Ereignis als Reaktion auf zeitgesteuerte Metadatenvorgänge.
title: Ereignisse für Werbeanzeigen/Zeitgesteuerte Metadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Ereignis für Anzeigen mit Bereitstellungs-/Zeitüberschreitung bei Metadaten{#ad-serving-timed-metadata-events}

TVSDK sendet Adserving-Ereignis als Reaktion auf zeitgesteuerte Metadatenvorgänge.

Um über alle entsprechenden Ereignis benachrichtigt zu werden, registrieren Sie Ereignis-Listener für die folgenden Ereignis beim `MediaPlayer`-Objekt.

| Ereignis | Bedeutung |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Es wurden ID3-zeitgesteuerte Metadaten verarbeitet. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Es wurden zeitgesteuerte Metadaten verarbeitet und keine Gelegenheit erkannt. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Zeitgesteuerte Metadaten sind verfügbar und es wurde keine Gelegenheit erkannt. |
| TimedMetadataEvent.[TIMED_METADATA_IN_HINTERGRUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Zeitgesteuerte Metadaten wurden verarbeitet und im Hintergrundmanifest wurde keine Gelegenheit erkannt. |