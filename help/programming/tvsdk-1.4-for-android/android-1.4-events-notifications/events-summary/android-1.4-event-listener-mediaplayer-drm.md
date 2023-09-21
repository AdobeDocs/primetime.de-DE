---
description: TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.
title: DRM-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# DRM-Ereignisse{#drm-events}

TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden.

Um über alle DRM-bezogenen Ereignisse informiert zu werden, registrieren Sie eine Implementierung von `MediaPlayer.DRMEventListener` , der den folgenden Rückruf enthält.

| Ereignis | Bedeutung |
|---|---|
| [onDRMMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.DRMEventListener.html#onDRMMetadata(DRMMetadataInfo)) `(DRMMetadataInfo drmMetadataInfo)` | Neue DRM-Metadaten sind verfügbar. |
