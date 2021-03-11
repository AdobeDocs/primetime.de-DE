---
description: Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.
title: Inspect der Wiedergabe-Timeline
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Inspect der Zeitleiste für die Wiedergabe{#inspect-the-playback-timeline}

Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.

Im Folgenden finden Sie eine Beispielimplementierung, wie im folgenden Screenshot gezeigt.  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Greifen Sie mithilfe der `getTimeline`-Methode auf das `Timeline`-Objekt in `MediaPlayer` zu.

   Die `Timeline`-Klasse enthält die Informationen zum Inhalt der Zeitleiste, die mit dem Medienelement verknüpft ist, das derzeit von der `MediaPlayer`-Instanz geladen wird. Die `Timeline`-Klasse bietet Zugriff auf eine schreibgeschützte Ansicht der zugrunde liegenden Zeitleiste. Die `Timeline`-Klasse stellt eine Getter-Methode bereit, die einen Iterator über eine Liste von `TimelineMarker`-Objekten bereitstellt.

1. Durchlaufen Sie die Liste von `TimelineMarkers` und verwenden Sie die zurückgegebenen Informationen, um Ihre Zeitschiene zu implementieren.

       Ein &quot;TimelineMarker&quot;-Objekt enthält zwei Informationen:
   
   * Position der Markierung auf der Zeitleiste (in Millisekunden)
   * Dauer der Markierung auf der Zeitleiste (in Millisekunden)

1. Implementieren Sie die Rückrufschnittstelle des Listeners `MediaPlayer.PlaybackEventListener.onTimelineUpdated` und registrieren Sie sie beim `Timeline`-Objekt.

   Das `Timeline`-Objekt kann Ihre Anwendung über Änderungen informieren, die in der Wiedergabedauer auftreten können, indem Sie den `OnTimelineUpdated`-Listener aufrufen.

```java
// access the timeline object 
Timeline timeline = mediaPlayer.getTimeline(); 
// iterate through the list of TimelineMarkers 
Iterator<TimelineMarker> iterator = timeline.timelineMarkers(); 
while (iterator.hasNext()) { 
   TimelineMarker marker = iterator.next(); 
   // the start position of the marker 
   long startPos = marker.getTime(); 
   // the duration of the marker 
   long duration = marker.getDuration(); 
}
```

