---
description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-title: Benutzerdefinierte Tags abonnieren
title: Benutzerdefinierte Tags abonnieren
uuid: 9f74b2b9-bbc9-433c-8226-2c2b68eddf7e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Benutzerdefinierte Tags abonnieren {#subscribe-to-custom-tags}

TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor den Wiedergabe-Beginn müssen Sie die Tags abonnieren. So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Legen Sie die benutzerdefinierten Tag-Namen global fest, indem Sie ein Array übergeben, das die benutzerdefinierten Tags enthält, zu `setSubscribedTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Beim Arbeiten mit HLS-Streams müssen Sie das `#` Präfix einschließen.

   Beispiel:

   ```java
   String[] array = new String[3]; 
   array[0] = "#EXT-X-ASSET"; 
   array[1] = "#EXT-X-BLACKOUT"; 
   array[2] = "#EXT-OATCLS-SCTE35"; 
   MediaPlayerItemConfig.setSubscribedTags(array);
   ```

