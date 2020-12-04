---
description: Die ReplaceTimeRange-Dienstprogrammklasse ist eine Erweiterung der TimeRange-Klasse, die mit CustomRangeMetadata verwendet wird.
seo-description: Die ReplaceTimeRange-Dienstprogrammklasse ist eine Erweiterung der TimeRange-Klasse, die mit CustomRangeMetadata verwendet wird.
seo-title: ReplaceTimeRange-Klasse
title: ReplaceTimeRange-Klasse
uuid: 19c49b26-5096-4429-b30b-bdd2502e3036
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---


# ReplaceTimeRange-Klasse {#replacetimerange-class}

Die ReplaceTimeRange-Dienstprogrammklasse ist eine Erweiterung der TimeRange-Klasse, die mit CustomRangeMetadata verwendet wird.

```java
public class ReplaceTimeRange extends TimeRange {
    // Default constructor method
    public ReplaceTimeRange() { 
        ... 
    }

    // Details of begining, duration and replaceDuration 
    // provided at construction time 
    public ReplaceTimeRange(long begin, long duration, long replaceDuration) { 
        ... 
    }

    // Replace duration
    public long getReplaceDuration() { 
        ... 
    }
}
```

