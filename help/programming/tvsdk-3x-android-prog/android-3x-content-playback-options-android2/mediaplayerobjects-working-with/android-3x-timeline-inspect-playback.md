---
description: Sie können eine Beschreibung der Timeline abrufen, die mit dem aktuell ausgewählten Element verknüpft ist, das von TVSDK wiedergegeben wird. Dies ist am nützlichsten, wenn Ihre Anwendung ein benutzerdefiniertes Scroll-Bar-Steuerelement anzeigt, in dem die Inhaltsbereiche identifiziert werden, die mit Anzeigeninhalten übereinstimmen.
title: Inspect der Wiedergabezeitleiste
exl-id: 95792354-76f6-44fd-9207-73e862b434e1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Inspect der Wiedergabezeitleiste {#inspect-the-playback-timeline}

Sie können eine Beschreibung der Timeline abrufen, die mit dem aktuell ausgewählten Element verknüpft ist, das von TVSDK wiedergegeben wird. Dies ist am nützlichsten, wenn Ihre Anwendung ein benutzerdefiniertes Scroll-Bar-Steuerelement anzeigt, in dem die Inhaltsbereiche identifiziert werden, die mit Anzeigeninhalten übereinstimmen.

Im Folgenden finden Sie eine Beispielimplementierung, wie im folgenden Screenshot gezeigt.  ![](assets/inspect-playback.jpg){width="368.641pt"}

1. Zugriff auf `Timeline` -Objekt im `MediaPlayer` mithilfe der `getTimeline()` -Methode.

   Die `Timeline` -Klasse kapselt die Informationen, die sich auf den Inhalt der Timeline beziehen, die mit dem Medienelement verknüpft ist, das derzeit von der `MediaPlayer` -Instanz. Die `Timeline` -Klasse bietet Zugriff auf eine schreibgeschützte Ansicht der zugrunde liegenden Timeline. Die `Timeline` -Klasse stellt eine Getter-Methode bereit, die einen Iterator über eine Liste von `TimelineMarker` Objekte.

1. Iterate through the list of `TimelineMarkers` und verwenden Sie die zurückgegebenen Informationen, um Ihre Timeline zu implementieren.

       Ein Objekt &quot;TimelineMarker&quot;enthält zwei Informationen:
   
   * Position der Markierung auf der Timeline (in Millisekunden)
   * Dauer der Markierung auf der Timeline (in Millisekunden)

1. Suchen Sie nach `MediaPlayerEvent.TIMELINE_UPDATED` -Ereignis auf `MediaPlayer` und implementieren Sie die `TimelineUpdatedEventListener.onTimelineUpdated()` Callback.

   Die `Timeline` -Objekt kann Ihre Anwendung über Änderungen in der Wiedergabe-Timeline informieren, indem Sie Ihre `OnTimelineUpdated` Listener.

```java
// access the timeline object 
Timeline timeline = mediaPlayer.getTimeline(); 
 
// Iterate through the list of TimelineMarkers 
Iterator<TimelineMarker> iterator = timeline.timelineMarkers(); 
 
while (iterator.hasNext()) { 
    TimelineMarker marker = iterator.next(); 
    // the start position of the marker 
    long startPos = marker.getTime(); 
    // the duration of the marker 
    long duration = marker.getDuration(); 
}
```
