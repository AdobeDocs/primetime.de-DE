---
description: Die ReplaceTimeRange-Dienstprogrammklasse ist eine Erweiterung der TimeRange-Klasse, die mit CustomRangeMetadata verwendet wird.
title: ReplaceTimeRange-Klasse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '36'
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

