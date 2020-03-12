---
description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-title: Benutzerdefinierte Tags abonnieren
title: Benutzerdefinierte Tags abonnieren
uuid: fe8ba34d-66fc-43bb-b98e-659c1702d1e0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Benutzerdefinierte Tags abonnieren{#subscribe-to-custom-tags}

TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor den Wiedergabe-Beginn müssen Sie die Tags abonnieren.
So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

Legen Sie die benutzerdefinierten Tag-Namen global fest, indem Sie ein Array übergeben, das die benutzerdefinierten Tags enthält, zu `setSubscribedTags` in `MediaPlayerItemConfig`.

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

