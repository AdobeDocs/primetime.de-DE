---
description: Um Benachrichtigungen zu Aktualisierungen der Zeitschiene zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.
seo-description: Um Benachrichtigungen zu Aktualisierungen der Zeitschiene zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.
seo-title: Hinzufügen Listener für TimelineUpdatedEvent
title: Hinzufügen Listener für TimelineUpdatedEvent
uuid: 7d742e15-5a55-4155-93a7-7b79f21c1472
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Hinzufügen Listener für TimelineUpdatedEvent{#add-listeners-for-timelineupdatedevent}

Um Benachrichtigungen zu Aktualisierungen der Zeitschiene zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.

Bei jeder Aktualisierung der Zeitschiene wird der `MediaPlayer` Text `AdobePSDK.TimelineEvent` mit Typ `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`gesendet.
1. Implementieren Sie die entsprechenden Listener.

   ```js
   function onTimelineUpdatedEvent(event) { 
       var timelineMarkers = event.timeline.timelineMarkers; 
       //add code to remove old timeline markers from scrub-bar. 
       var range = player.playbackRange; 
       //iterate through the list of timelineMarkers 
       for(var i = 0; i < timelineMarkers.length; i++) 
       { 
           var markerLocalTime = timelineMarkers[i].localRange.begin; 
           var markerVirtualTime = timelineMarkers[i].virtualRange.begin; 
           var duration = timelineMarkers[i].duration; 
        // add code to draw a particular marker on scrub-bar 
       }      
   }
   ```

1. Registrieren Sie die Ereignis-Listener.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMELINE_UPDATED,  
       onTimelineUpdatedEvent);
   ```

