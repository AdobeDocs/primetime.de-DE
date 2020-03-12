---
description: TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-description: TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-title: Benutzerdefinierte Tags abonnieren
title: Benutzerdefinierte Tags abonnieren
uuid: e47076b2-6184-4c20-bae4-ba7ae62cf198
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Benutzerdefinierte Tags abonnieren {#subscribe-to-custom-tags}

TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor den Wiedergabe-Beginn müssen Sie die Tags abonnieren.
So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Legen Sie die benutzerdefinierten Tag-Namen global fest, indem Sie ein Array übergeben, das die benutzerdefinierten Tags enthält, zu `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >Beim Arbeiten mit HLS-Streams müssen Sie das `#` Präfix einschließen.

   Beispiel:

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```
