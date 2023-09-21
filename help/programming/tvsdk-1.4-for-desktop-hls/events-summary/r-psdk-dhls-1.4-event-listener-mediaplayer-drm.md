---
description: TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.
title: DRM-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# DRM-Ereignisse{#drm-events}

TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.

Um über alle DRM-bezogenen Ereignisse benachrichtigt zu werden, suchen Sie nach `DRMMetadataInfoEvent` für DRM-Ereignisse mit der `MediaPlayer` -Objekt.

| Ereignis | Bedeutung |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | Neue DRM-Metadaten sind verfügbar. |
