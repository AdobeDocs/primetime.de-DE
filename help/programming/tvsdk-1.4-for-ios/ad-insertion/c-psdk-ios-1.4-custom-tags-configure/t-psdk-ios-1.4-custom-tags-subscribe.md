---
description: TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-description: TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-title: Benutzerdefinierte Tags abonnieren
title: Benutzerdefinierte Tags abonnieren
uuid: de66d3db-46d1-485f-9d3a-6e28495bfb13
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 1%

---


# Benutzerdefinierte Tags abonnieren {#subscribe-to-custom-tags}

TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor den Wiedergabe-Beginn müssen Sie die Tags abonnieren.
So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Stellen Sie die benutzerdefinierten Tag-Namen global ein, indem Sie ein Array mit den benutzerdefinierten Tags an `setSubscribedTags` in `PTSDKConfig` übergeben.

   >[!IMPORTANT]
   >
   >Sie müssen beim Arbeiten mit HLS-Streams das Präfix `#` einschließen.

   Beispiel:

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```

