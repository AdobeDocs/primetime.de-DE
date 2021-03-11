---
description: Die TimeRangeCollection-Dienstprogrammklasse fasst die Vorstellung einer geordneten Auflistung von TimeRange-Spezifikationen zusammen und stellt Dienste bereit, die sich selbst in eine Metadateninstanz übersetzen.
title: TimeRangeCollection-Klasse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# TimeRangeCollection-Klasse{#timerangecollection-class}

Die TimeRangeCollection-Dienstprogrammklasse fasst die Vorstellung einer geordneten Auflistung von TimeRange-Spezifikationen zusammen und stellt Dienste bereit, die sich selbst in eine Metadateninstanz übersetzen.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```java
public final class TimeRangeCollection {
    // default constructor method
    public TimeRangeCollection(Type type) {...}

    // the list of timerange specifications provided at construction time 
    public TimeRangeCollection(Type type, List<TimeRange> timeRanges) {...}

    // timerange specs can also be added later
    public void addTimeRange(TimeRange timeRange) {...}

    // translate the set of timerange specs into a Metadata instance 
    public Metadata toMetadata(Metadata options) {...}
}
```

Der Parameter `type`, der erste Positionsparameter in der Signatur der Konstruktormethoden, ist eine Instanz der Auflistung `TimeRangeCollection#Type`. Dies ist Teil der `TimeRangeCollection`-Klasse. Die Werte, die derzeit von dieser Auflistung definiert werden, sind `MARK_RANGES`, `DELETE_RANGES` und `REPLACE_RANGES`. Sie können `TimeRangeCollection`-Objekte mit diesen drei Typen erstellen.
