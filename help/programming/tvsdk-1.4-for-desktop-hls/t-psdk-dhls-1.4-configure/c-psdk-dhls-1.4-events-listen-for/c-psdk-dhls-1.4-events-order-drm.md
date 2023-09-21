---
description: TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann als Reaktion auf diese Ereignisse Aktionen implementieren.
title: DRM-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# DRM-Ereignisse{#drm-events}

TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann als Reaktion auf diese Ereignisse Aktionen implementieren.

Um über alle DRM-bezogenen Ereignisse benachrichtigt zu werden, achten Sie auf Folgendes:

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
