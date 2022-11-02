---
description: Sie können eine Beschreibung der Timeline abrufen, die mit dem aktuell ausgewählten Element verknüpft ist, das von TVSDK wiedergegeben wird. Dies ist am nützlichsten, wenn Ihre Anwendung ein benutzerdefiniertes Scroll-Bar-Steuerelement anzeigt, in dem die Inhaltsbereiche identifiziert werden, die mit Anzeigeninhalten übereinstimmen.
title: Inspect der Wiedergabezeitleiste
exl-id: 38b5ce0e-5554-462e-986f-f3864f7cf879
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Inspect der Wiedergabezeitleiste{#inspect-the-playback-timeline}

Sie können eine Beschreibung der Timeline abrufen, die mit dem aktuell ausgewählten Element verknüpft ist, das von TVSDK wiedergegeben wird. Dies ist am nützlichsten, wenn Ihre Anwendung ein benutzerdefiniertes Scroll-Bar-Steuerelement anzeigt, in dem die Inhaltsbereiche identifiziert werden, die mit Anzeigeninhalten übereinstimmen.

Im Folgenden finden Sie eine Beispielimplementierung, wie im folgenden Screenshot gezeigt.
<!--<a id="fig_6D9FB3764F3947A38B8E7726187BD461"></a>-->

![](assets/inspect-playback.jpg){width="368.641pt"}

1. Zugriff auf `Timeline` -Objekt im `MediaPlayer` mithilfe der `get` -Methode.

   Die `Timeline` -Klasse kapselt die Informationen, die sich auf den Inhalt der Timeline beziehen, die mit dem Medienelement verknüpft ist, das derzeit von der `MediaPlayer` -Instanz. Die `Timeline` -Klasse bietet Zugriff auf eine schreibgeschützte Ansicht der zugrunde liegenden Timeline. Die `Timeline` -Klasse bietet eine Getter-Methode zum Abrufen aller platzierten `TimelineMarker` Objekte.

1. Iterate through the list of `TimelineMarkers` und verwenden Sie die zurückgegebenen Informationen, um Ihre Timeline zu implementieren.

       Ein Objekt &quot;TimelineMarker&quot;enthält zwei Informationen:
   
   * Position der Markierung auf der Timeline (in Millisekunden)
   * Dauer der Markierung auf der Timeline (in Millisekunden)

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
