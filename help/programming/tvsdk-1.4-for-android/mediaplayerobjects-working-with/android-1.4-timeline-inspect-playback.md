---
description: Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.
seo-description: Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.
seo-title: Überprüfen der Zeitleiste für die Wiedergabe
title: Überprüfen der Zeitleiste für die Wiedergabe
uuid: b5ede131-1037-449b-bc3f-a066fdc92fc5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Überprüfen der Zeitleiste für die Wiedergabe{#inspect-the-playback-timeline}

Sie können eine Beschreibung der Zeitschiene abrufen, die mit dem derzeit ausgewählten Element, das von TVSDK wiedergegeben wird, verknüpft ist. Dies ist besonders hilfreich, wenn Ihre Anwendung ein benutzerdefiniertes Scrubbing-Bar-Steuerelement anzeigt, in dem die Inhaltsabschnitte, die mit dem Anzeigeninhalt übereinstimmen, identifiziert werden.

Im Folgenden finden Sie eine Beispielimplementierung, wie im folgenden Screenshot gezeigt.  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Greifen Sie auf das `Timeline` Objekt in der `MediaPlayer` Methode mit der `getTimeline` Methode zu.

   Die `Timeline` Klasse kapselt die Informationen zum Inhalt der Zeitleiste, die mit dem Medienelement verknüpft ist, das derzeit von der `MediaPlayer` Instanz geladen wird. Die `Timeline` Klasse bietet Zugriff auf eine schreibgeschützte Ansicht der zugrunde liegenden Zeitleiste. Die `Timeline` Klasse stellt eine Getter-Methode bereit, die einen Iterator über eine Liste von `TimelineMarker` Objekten bereitstellt.

1. Durchlaufen Sie die Liste der zurückgegebenen Informationen `TimelineMarkers` und verwenden Sie sie, um Ihre Zeitschiene zu implementieren.

       Ein &quot;TimelineMarker&quot;-Objekt enthält zwei Informationen:
   
   * Position der Markierung auf der Zeitleiste (in Millisekunden)
   * Dauer der Markierung auf der Zeitleiste (in Millisekunden)

1. Implementieren Sie die Rückruffunktion für den Listener `MediaPlayer.PlaybackEventListener.onTimelineUpdated` und registrieren Sie sie beim `Timeline` Objekt.

   Das `Timeline` Objekt kann Ihre Anwendung über Änderungen informieren, die in der Zeitleiste der Wiedergabe auftreten können, indem Sie Ihren `OnTimelineUpdated` Listener aufrufen.

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

