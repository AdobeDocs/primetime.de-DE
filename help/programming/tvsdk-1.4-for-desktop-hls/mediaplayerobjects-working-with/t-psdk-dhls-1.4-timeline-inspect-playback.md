---
description: Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.
seo-description: Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.
seo-title: Überprüfen der Zeitleiste für die Wiedergabe
title: Überprüfen der Zeitleiste für die Wiedergabe
uuid: 2f903493-2d88-4af2-ac71-36300b49735b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Überprüfen der Zeitleiste für die Wiedergabe{#inspect-the-playback-timeline}

Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.

Im Folgenden finden Sie eine Beispielimplementierung, wie im folgenden Screenshot gezeigt.
<!--<a id="fig_6D9FB3764F3947A38B8E7726187BD461"></a>-->

![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Greifen Sie auf das `Timeline` Objekt in der `MediaPlayer` Methode mit der `get` Methode zu.

   Die `Timeline` Klasse kapselt die Informationen zum Inhalt der Zeitleiste, die mit dem Medienelement verknüpft ist, das derzeit von der `MediaPlayer` Instanz geladen wird. Die `Timeline` Klasse bietet Zugriff auf eine schreibgeschützte Ansicht der zugrunde liegenden Zeitleiste. Die `Timeline` Klasse stellt eine Getter-Methode zum Abrufen aller platzierten `TimelineMarker` Objekte bereit.

1. Durchlaufen Sie die Liste der zurückgegebenen Informationen `TimelineMarkers` und verwenden Sie sie, um Ihre Zeitschiene zu implementieren.

       Ein &quot;TimelineMarker&quot;-Objekt enthält zwei Informationen:
   
   * Position der Markierung auf der Zeitleiste (in Millisekunden)
   * Dauer der Markierung auf der Zeitleiste (in Millisekunden)

<!--<a id="example_BA936629E82B4082A2E2C548E3FC3357"></a>-->

```
// access the timeline object 
var timeline:Timeline = mediaPlayer.timeline; 
 
// iterate through the list of TimelineMarkers 
var markers:Vector.<TimelineMarker> = timeline.timelineMarkers; 
markers.forEach(function(item:TimelineMarker,  
                         index:int,  
                         vector:Vector.<TimelineMarker>):void { 
    
    // the start position of the marker 
    var startPos:Number = item.time; 
 
    // the duration of the marker 
    var duration:Number = item.duration; 
 
    // draw the marker on the scrub-bar 
}
```

