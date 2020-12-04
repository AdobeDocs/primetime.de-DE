---
description: Die TimeRangeCollection-Dienstprogrammklasse fasst die Vorstellung einer geordneten Auflistung von TimeRange-Spezifikationen zusammen und stellt Dienste bereit, die sich selbst in eine Metadateninstanz übersetzen.
seo-description: Die TimeRangeCollection-Dienstprogrammklasse fasst die Vorstellung einer geordneten Auflistung von TimeRange-Spezifikationen zusammen und stellt Dienste bereit, die sich selbst in eine Metadateninstanz übersetzen.
seo-title: TimeRangeCollection-Klasse
title: TimeRangeCollection-Klasse
uuid: da781df4-6b19-47e1-8dc5-ea83c139f061
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# TimeRangeCollection-Klasse{#timerangecollection-class}

Die TimeRangeCollection-Dienstprogrammklasse fasst die Vorstellung einer geordneten Auflistung von TimeRange-Spezifikationen zusammen und stellt Dienste bereit, die sich selbst in eine Metadateninstanz übersetzen.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

Der definierte Wert für den Sammlungstyp sind `MARK_RANGES`, `DELETE_RANGES` und `REPLACE_RANGES`. Sie können `TimeRangeCollection`s mit diesen drei Typen erstellen.
