---
description: Um Benachrichtigungen zu Aktualisierungen der Zeitschiene zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.
title: hinzufügen Listener für TimelineUpdatedEvent
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# hinzufügen Listener für TimelineUpdatedEvent{#add-listeners-for-timelineupdatedevent}

Um Benachrichtigungen zu Aktualisierungen der Zeitschiene zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.

Bei jeder Aktualisierung der Zeitleiste löst `MediaPlayer` `AdobePSDK.TimelineEvent` den Wert `AdobePSDK.PSDKEventType.TIMELINE_UPDATED` aus.
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

