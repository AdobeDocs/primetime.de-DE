---
description: TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.
title: DRM-Ereignisse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# DRM-Ereignis{#drm-events}

TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.

Um über alle DRM-bezogenen Ereignis benachrichtigt zu werden, suchen Sie nach `DRMMetadataInfoEvent` für DRM-Ereignis mit dem `MediaPlayer`-Objekt.

| Ereignis | Bedeutung |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | Es sind neue DRM-Metadaten verfügbar. |