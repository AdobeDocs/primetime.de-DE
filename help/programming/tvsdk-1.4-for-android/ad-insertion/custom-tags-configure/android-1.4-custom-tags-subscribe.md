---
description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
title: Benutzerdefinierte Tags abonnieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Benutzerdefinierte Tags abonnieren{#subscribe-to-custom-tags}

TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor dem Start der Wiedergabe müssen Sie die Tags abonnieren.
So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

Globales Festlegen der benutzerdefinierten Anzeigen-Tag-Namen durch Übergabe eines Arrays, das die benutzerdefinierten Tags enthält an `setSubscribedTags` in `MediaPlayerItemConfig`.

>[!IMPORTANT]
>
>Sie müssen die `#` Präfix beim Arbeiten mit HLS-Streams.

Beispiel:

```java
String[] array = new String[3]; 
array[0] = "#EXT-X-ASSET"; 
array[1] = "#EXT-X-BLACKOUT"; 
array[2] = "#EXT-OATCLS-SCTE35"; 
MediaPlayerItemConfig.setSubscribedTags(array);
```
