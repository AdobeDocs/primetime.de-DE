---
description: TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann entsprechend diesen Ereignissen Aktionen implementieren.
seo-description: TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann entsprechend diesen Ereignissen Aktionen implementieren.
seo-title: DRM-Ereignisse
title: DRM-Ereignisse
uuid: 729fe524-1047-4188-b4e6-96bfc5af4ae0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# DRM-Ereignisse{#drm-events}

TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann entsprechend diesen Ereignissen Aktionen implementieren.

Um über alle DRM-bezogenen Ereignis informiert zu werden, beachten Sie Folgendes:

```
DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE
```

Das folgende Beispiel zeigt eine typische Progression:

```
mediaPlayer.addEventListener(DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE,  
                             onDRMMetadataInfoAvailable);   
private function onDRMMetadataInfoAvailable(event:DRMMetadataInfoEvent){ 
    var drmMetadataInfo:DRMMetadataInfo = event.drmMetadataInfo; 
    ... 
} 
```

