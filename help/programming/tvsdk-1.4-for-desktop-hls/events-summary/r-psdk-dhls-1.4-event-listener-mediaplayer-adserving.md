---
description: TVSDK sendet Adserving-Ereignis als Reaktion auf zeitgesteuerte Metadatenvorgänge.
seo-description: TVSDK sendet Adserving-Ereignis als Reaktion auf zeitgesteuerte Metadatenvorgänge.
seo-title: Ereignisse für Werbeanzeigen/Zeitgesteuerte Metadaten
title: Ereignisse für Werbeanzeigen/Zeitgesteuerte Metadaten
uuid: fd50a937-0c9b-4c47-acb2-1ffc0592ad54
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Ereignisse für Werbeanzeigen/Zeitgesteuerte Metadaten{#ad-serving-timed-metadata-events}

TVSDK sendet Adserving-Ereignis als Reaktion auf zeitgesteuerte Metadatenvorgänge.

Um über alle entsprechenden Ereignis benachrichtigt zu werden, registrieren Sie Ereignis-Listener für die folgenden Ereignis beim `MediaPlayer` Objekt.

| Ereignis | Bedeutung |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Es wurden ID3-zeitgesteuerte Metadaten verarbeitet. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Es wurden zeitgesteuerte Metadaten verarbeitet und keine Gelegenheit erkannt. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Zeitgesteuerte Metadaten sind verfügbar und es wurde keine Gelegenheit erkannt. |
| TimedMetadataEvent.[TIMED_METADATA_IN_HINTERGRUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Zeitgesteuerte Metadaten wurden verarbeitet und im Hintergrundmanifest wurde keine Gelegenheit erkannt. |