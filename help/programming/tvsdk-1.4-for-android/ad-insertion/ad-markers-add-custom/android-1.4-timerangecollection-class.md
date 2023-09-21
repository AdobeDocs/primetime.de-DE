---
description: Die Dienstprogrammklasse TimeRangeCollection stellt die Vorstellung einer geordneten Sammlung von TimeRange-Spezifikationen dar und bietet Dienste, um sich selbst in eine Metadaten-Instanz zu übersetzen.
title: TimeRangeCollection-Klasse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# TimeRangeCollection-Klasse{#timerangecollection-class}

Die Dienstprogrammklasse TimeRangeCollection stellt die Vorstellung einer geordneten Sammlung von TimeRange-Spezifikationen dar und bietet Dienste, um sich selbst in eine Metadaten-Instanz zu übersetzen.

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

Die `type` -Parameter, der den ersten Positionsparameter in der Signatur der Konstruktormethoden darstellt, ist eine Instanz der `TimeRangeCollection#Type` -Auflistung. Dies ist Teil der `TimeRangeCollection` -Klasse. Die Werte, die derzeit von dieser Auflistung definiert werden, sind `MARK_RANGES`, `DELETE_RANGES`, und `REPLACE_RANGES`. Sie können `TimeRangeCollection` Objekte, die diese drei Typen verwenden.
