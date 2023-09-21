---
description: TVSDK sendet Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen in der erwarteten Sequenz implementieren.
title: Reihenfolge der Wiedergabeereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Reihenfolge der Wiedergabeereignisse{#order-of-playback-events}

TVSDK sendet Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen in der erwarteten Sequenz implementieren.

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

Die folgenden Beispiele zeigen die Reihenfolge einiger Ereignisse, die Wiedergabeereignisse enthalten.

* Beim erfolgreichen Laden einer Medienressource über `MediaPlayer.replaceCurrentResource`lautet die Reihenfolge der Ereignisse:

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.INITIALIZED`

* Beim Vorbereiten der Wiedergabe über `MediaPlayer.prepareToPlay`lautet die Reihenfolge der Ereignisse:

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` , wenn Anzeigen eingefügt wurden
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.PREPARED`

* Bei Live-/linearen Streams lautet die Reihenfolge der Ereignisse während der Wiedergabe, während das Wiedergabefenster wechselt und zusätzliche Möglichkeiten aufgelöst werden:

   * `MediaPlayerItemEvent.ITEM_UPDATED`
   * `TimelineEvent.TIMELINE_UPDATED` , wenn Anzeigen eingefügt wurden

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

Das folgende Beispiel zeigt eine typische Progression von Ereignissen:

```
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
public function onItemCreated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
public function onItemUpdated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
public function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    switch(event.status){ 
        case MediaPlayerStatus.INITIALIZING: 
        case MediaPlayerStatus.INITIALIZED: 
        ... 
    } 
    ... 
} 
mediaPlayer.addEventListener(TimeChangeEvent.TIME_CHANGED, onTimeChanged); 
public function onTimeChanged(event:TimeChangeEvent):void { 
    var timeInMilliseconds:Number = event.time; 
    ... 
}
```
