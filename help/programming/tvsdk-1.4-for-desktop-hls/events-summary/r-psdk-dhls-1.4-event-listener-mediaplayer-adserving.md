---
description: TVSDK sendet Adserving-Ereignisse als Reaktion auf zeitgesteuerte Metadatenvorgänge.
title: Anzeigen-Serving/zeitgesteuerte Metadatenereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Anzeigen-Serving/zeitgesteuerte Metadatenereignisse{#ad-serving-timed-metadata-events}

TVSDK sendet Adserving-Ereignisse als Reaktion auf zeitgesteuerte Metadatenvorgänge.

Um über alle derartigen Ereignisse benachrichtigt zu werden, registrieren Sie Ereignis-Listener bei der `MediaPlayer` -Objekt für die folgenden Ereignisse.

| Ereignis | Bedeutung |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Zeitgesteuerte Metadaten für ID3 wurden verarbeitet. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Es wurden zeitgesteuerte Metadaten verarbeitet und keine Möglichkeit erkannt. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Zeitgesteuerte Metadaten sind verfügbar und es wurde keine Gelegenheit erkannt. |
| TimedMetadataEvent.[TIMED_METADATA_IN_HINTERGRUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Zeitgesteuerte Metadaten wurden verarbeitet und im Hintergrundmanifest wurde keine Gelegenheit erkannt. |
