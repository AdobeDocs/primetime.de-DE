---
description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
title: Benutzerdefinierte Tags abonnieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

---


# Benutzerdefinierte Tags abonnieren {#subscribe-to-custom-tags}

TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor den Wiedergabe-Beginn müssen Sie die Tags abonnieren. So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Stellen Sie die benutzerdefinierten Tag-Namen global ein, indem Sie ein Array mit den benutzerdefinierten Tags an `setSubscribedTags` in `MediaPlayerItemConfig` übergeben.

   >[!IMPORTANT]
   >
   >Sie müssen beim Arbeiten mit HLS-Streams das Präfix `#` einschließen.

   Beispiel:

   ```java
   String[] array = new String[3]; 
   array[0] = "#EXT-X-ASSET"; 
   array[1] = "#EXT-X-BLACKOUT"; 
   array[2] = "#EXT-OATCLS-SCTE35"; 
   MediaPlayerItemConfig.setSubscribedTags(array);
   ```
