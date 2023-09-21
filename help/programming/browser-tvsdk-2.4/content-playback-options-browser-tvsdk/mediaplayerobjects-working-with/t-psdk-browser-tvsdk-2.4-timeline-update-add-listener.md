---
description: Um Benachrichtigungen zu Timeline-Aktualisierungen zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.
title: Listener für TimelineUpdatedEvent hinzufügen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Listener für TimelineUpdatedEvent hinzufügen{#add-listeners-for-timelineupdatedevent}

Um Benachrichtigungen zu Timeline-Aktualisierungen zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.

Bei jeder Aktualisierung der Timeline wird die `MediaPlayer` dispatches `AdobePSDK.TimelineEvent` mit Typ `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`.
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
