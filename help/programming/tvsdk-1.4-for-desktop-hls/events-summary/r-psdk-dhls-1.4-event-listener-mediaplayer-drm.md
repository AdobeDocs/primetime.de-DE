---
description: TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.
seo-description: TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.
seo-title: DRM-Ereignisse
title: DRM-Ereignisse
uuid: f1da5b31-3fad-4bb4-8aa3-3925d5f0e123
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# DRM-Ereignis{#drm-events}

TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.

Um über alle DRM-bezogenen Ereignis benachrichtigt zu werden, suchen Sie nach `DRMMetadataInfoEvent` für DRM-Ereignis mit dem `MediaPlayer`-Objekt.

| Ereignis | Bedeutung |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | Es sind neue DRM-Metadaten verfügbar. |