---
description: Wenn Ihre Wiedergabe Werbung enthält, sendet TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.
title: Reihenfolge der Ereignis
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Reihenfolge der Ereignis für Werbung{#order-of-advertising-events}

Wenn Ihre Wiedergabe Werbung enthält, sendet TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignis:

* `AdBreakPlaybackEvent.AD_BREAK_STARTED`
* Für jede Anzeige in der Werbeunterbrechung werden die folgenden Meldungen ausgelöst:

   * `AdPlaybackEvent.AD_STARTED`
   * `AdPlaybackEvent.AD_PROGRESS` (mehrere Male während der Wiedergabe einer Anzeige)
   * `AdClickEvent.AD_CLICK` (für jeden Klick)
   * `AdPlaybackEvent.AD_COMPLETED`

* `AdBreakPlaybackEvent.AD_BREAK_COMPLETED`

Das folgende Beispiel zeigt eine typische Progression von Ereignissen zur Anzeigenwiedergabe:

```
mediaPlayer.addEventListener(AdBreakPlaybackEvent.AD_BREAK_STARTED, onAdBreakStarted); 
private function onAdBreakStarted(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    ... 
} 
mediaPlayer.addEventListener(AdBreakPlaybackEvent.AD_BREAK_COMPLETED, onAdBreakCompleted); 
private function onAdBreakCompleted(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_STARTED, onAdStarted); 
private function onAdStarted(event:AdPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_PROGRESS, onAdProgress); 
private function onAdProgress(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad;  
    var progress:uint = event.progress; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_COMPLETED, onAdCompleted); 
private function onAdCompleted(event:AdPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    ... 
} 
mediaPlayer.addEventListener(AdClickEvent.AD_CLICK, onAdClick); 
private function onAdClick(event:AdClickThroughEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    var info:AdClick = event.adClick; 
    ... 
} 
```

