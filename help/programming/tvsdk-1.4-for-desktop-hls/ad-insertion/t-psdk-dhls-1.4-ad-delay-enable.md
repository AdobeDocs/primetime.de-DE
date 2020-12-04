---
description: Sie können angeben, ob die Wiedergabe zulässig ist, bevor alle Anzeigen geladen und in die Zeitleiste platziert werden. Die Wiedergabe auf diese Weise zu starten, ermöglicht einem Viewer einen schnelleren Zugriff auf den Hauptinhalt. Diese Funktion ist nur für Live-DVR verfügbar und funktioniert nicht, z. B. bei VOD-Assets.
seo-description: Sie können angeben, ob die Wiedergabe zulässig ist, bevor alle Anzeigen geladen und in die Zeitleiste platziert werden. Die Wiedergabe auf diese Weise zu starten, ermöglicht einem Viewer einen schnelleren Zugriff auf den Hauptinhalt. Diese Funktion ist nur für Live-DVR verfügbar und funktioniert nicht, z. B. bei VOD-Assets.
seo-title: Verzögertes Laden von Anzeigen aktivieren
title: Verzögertes Laden von Anzeigen aktivieren
uuid: ac7c8801-7fa2-4f17-b79c-c603b3236948
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# Verzögertes Laden der Anzeige aktivieren{#enable-lazy-ad-loading}

Sie können angeben, ob die Wiedergabe zulässig ist, bevor alle Anzeigen geladen und in die Zeitleiste platziert werden. Die Wiedergabe auf diese Weise zu starten, ermöglicht einem Viewer einen schnelleren Zugriff auf den Hauptinhalt. Diese Funktion ist nur für Live-DVR verfügbar und funktioniert nicht, z. B. bei VOD-Assets.

1. Verwenden Sie die boolesche Eigenschaft `delayAdLoading` in `AdvertisingMetadata`.

   * Bei &quot;false&quot;wartet TVSDK, bis alle Anzeigen aufgelöst und platziert wurden, bevor zum Status &quot;VORBEREITT&quot;übergegangen wird. Der Standardwert lautet false.
   * Wenn &quot;true&quot;, löst TVSDK nur die anfänglichen Anzeigen und Transitionen auf den Status &quot;VORBEREITT&quot;auf. Die verbleibenden Anzeigen werden während der Wiedergabe aufgelöst und platziert.

1. Um auch verzögertes Laden der Anzeige bei der Adobe Primetime-Anzeigenentscheidung zu aktivieren, setzen Sie diese auf `true`, wenn Sie `AuditudeSettings` erstellen.

   Die `AuditudeSettings`-Klasse erbt diese Eigenschaft von `AdvertisingMetadata`, übernimmt jedoch nicht den aktuellen Wert.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. Um Anzeigen als Hinweise auf einer Scrubbing-Leiste genau wiederzugeben, sollten Sie auf `TimelineEvent` achten. `TIMELINE_UPDATED` ereignis und zeichnen Sie die Scrubbing-Leiste jedes Mal, wenn Sie dieses Ereignis erhalten.

   Wenn VoD-Streams verzögertes Laden von Anzeigen verwenden, werden nicht alle Anzeigen auf der Zeitleiste platziert, wenn Ihr Player den Status &quot;VORBEREITT&quot;aufruft. Daher müssen Sie die Scrubbing-Leiste explizit neu zeichnen.

   TVSDK optimiert den Versand dieses Ereignisses, um die Anzahl der Male zu minimieren, die Sie die Scrubbing-Leiste neu zeichnen müssen. Daher steht die Anzahl der Zeitschienen-Ereignis nicht in Zusammenhang mit der Anzahl der Werbeunterbrechungen, die auf der Zeitschiene platziert werden sollen. Wenn Sie beispielsweise fünf Werbeunterbrechungen haben, erhalten Sie möglicherweise nicht genau fünf Ereignis.

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```

