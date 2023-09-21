---
description: Die Dienstprogrammklasse TimeRangeCollection stellt die Vorstellung einer geordneten Sammlung von TimeRange-Spezifikationen dar und bietet Dienste, um sich selbst in eine Metadaten-Instanz zu übersetzen.
title: TimeRangeCollection-Klasse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---

# TimeRangeCollection-Klasse{#timerangecollection-class}

Die Dienstprogrammklasse TimeRangeCollection stellt die Vorstellung einer geordneten Sammlung von TimeRange-Spezifikationen dar und bietet Dienste, um sich selbst in eine Metadaten-Instanz zu übersetzen.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

Der definierte Wert für den Sammlungstyp ist `MARK_RANGES`, `DELETE_RANGES`, und `REPLACE_RANGES`. Sie können `TimeRangeCollection`verwendet diese drei Typen.
