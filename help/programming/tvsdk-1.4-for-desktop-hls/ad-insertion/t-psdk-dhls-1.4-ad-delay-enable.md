---
description: Sie können angeben, ob die Wiedergabe zulässig ist, bevor alle Anzeigen geladen und in die Timeline platziert werden. Durch den Start der Wiedergabe auf diese Weise erhält ein Betrachter schneller Zugriff auf den Hauptinhalt. Diese Funktion ist nur für Live-DVR verfügbar und funktioniert nicht mit, sagen wir VOD-Assets.
title: Verzögertes Laden von Anzeigen aktivieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Verzögertes Laden von Anzeigen aktivieren{#enable-lazy-ad-loading}

Sie können angeben, ob die Wiedergabe zulässig ist, bevor alle Anzeigen geladen und in die Timeline platziert werden. Durch den Start der Wiedergabe auf diese Weise erhält ein Betrachter schneller Zugriff auf den Hauptinhalt. Diese Funktion ist nur für Live-DVR verfügbar und funktioniert nicht mit, sagen wir VOD-Assets.

1. Verwenden der booleschen Eigenschaft `delayAdLoading` in `AdvertisingMetadata`.

   * Bei &quot;false&quot;wartet TVSDK, bis alle Anzeigen aufgelöst und platziert werden, bevor zum Status VORBEREITT übergegangen wird. Der Standardwert ist &quot;false&quot;.
   * Wenn &quot;true&quot;, löst TVSDK nur die ersten Anzeigen auf und wechselt in den Status VORBEREITT . Die verbleibenden Anzeigen werden während der Wiedergabe aufgelöst und platziert.

1. Um auch verzögertes Laden von Anzeigen mit Adobe Primetime-Anzeigenentscheidungen zu aktivieren, setzen Sie dies auf `true` bei der Erstellung `AuditudeSettings`.

   Die `AuditudeSettings` -Klasse erbt diese Eigenschaft von `AdvertisingMetadata`, übernimmt jedoch nicht den aktuellen Wert.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. Um Anzeigen als Hinweise auf einer Scrubbing-Leiste genau wiederzugeben, sollten Sie auf die `TimelineEvent`. `TIMELINE_UPDATED` -Ereignis und zeichnen Sie die Scrub-Leiste jedes Mal neu, wenn Sie dieses Ereignis erhalten.

   Wenn VoD-Streams verzögertes Laden von Anzeigen verwenden, werden nicht alle Anzeigen auf der Timeline platziert, wenn Ihr Player in den Status VORBEREITT wechselt. Daher müssen Sie die Scrubbing-Leiste explizit neu zeichnen.

   TVSDK optimiert den Versand dieses Ereignisses, um die Häufigkeit zu minimieren, mit der Sie die Scrubbing-Leiste neu zeichnen müssen. Daher hängt die Anzahl der Timeline-Ereignisse nicht mit der Anzahl der Werbeunterbrechungen zusammen, die auf der Timeline platziert werden sollen. Wenn Sie beispielsweise fünf Werbeunterbrechungen haben, erhalten Sie möglicherweise nicht genau fünf Ereignisse.

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```
