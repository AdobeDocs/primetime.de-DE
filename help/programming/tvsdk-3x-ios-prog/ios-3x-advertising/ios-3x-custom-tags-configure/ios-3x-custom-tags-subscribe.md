---
description: TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
title: Benutzerdefinierte Tags abonnieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Benutzerdefinierte Tags abonnieren {#subscribe-to-custom-tags}

TVSDK bereitet PTTimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor dem Start der Wiedergabe müssen Sie die Tags abonnieren.
So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Globales Festlegen der benutzerdefinierten Anzeigen-Tag-Namen durch Übergabe eines Arrays, das die benutzerdefinierten Tags enthält an `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >Sie müssen die `#` Präfix beim Arbeiten mit HLS-Streams.

   Beispiel:

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```
