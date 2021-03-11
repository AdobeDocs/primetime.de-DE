---
description: TVSDK sendet Ereignis/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.
title: Reihenfolge der Ereignis
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# Reihenfolge der Ereignis für die Wiedergabe{#order-of-playback-events}

TVSDK sendet Ereignis/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

Die folgenden Beispiele zeigen die Reihenfolge einiger Ereignis, die Ereignis für die Wiedergabe enthalten.

* Beim erfolgreichen Laden einer Medienressource über `MediaPlayer.replaceCurrentResource` lautet die Reihenfolge der Ereignis:

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.INITIALIZED`

* Beim Vorbereiten der Wiedergabe über `MediaPlayer.prepareToPlay` lautet die Reihenfolge der Ereignis:

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` wenn Anzeigen eingefügt wurden
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.PREPARED`

* Bei Live-/linearen Streams lautet die Reihenfolge der Ereignis während der Wiedergabe, während das Wiedergabefenster erweitert und weitere Möglichkeiten aufgelöst werden, wie folgt:

   * `MediaPlayerItemEvent.ITEM_UPDATED`
   * `TimelineEvent.TIMELINE_UPDATED` wenn Anzeigen eingefügt wurden

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

