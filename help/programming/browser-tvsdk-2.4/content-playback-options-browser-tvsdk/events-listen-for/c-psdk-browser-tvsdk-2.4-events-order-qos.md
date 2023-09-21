---
description: Browser TVSDK sendet Servicequalitätsereignisse (QoS), um Ihre Anwendung über Ereignisse zu informieren, die die Berechnung von QoS-Statistiken beeinflussen könnten, z. B. Pufferungs- und Suchereignisse.
title: QoS-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# QoS-Ereignisse{#qos-events}

Browser TVSDK sendet Servicequalitätsereignisse (QoS), um Ihre Anwendung über Ereignisse zu informieren, die die Berechnung von QoS-Statistiken beeinflussen könnten, z. B. Pufferungs- und Suchereignisse.

Um über alle QoS-bezogenen Ereignisse benachrichtigt zu werden, erstellen Sie eine Instanz von `AdobePSDK.QOSProvider` und hängen Sie die MediaPlayer-Instanz an diese an `QOSProvider` instance:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Konfigurieren Sie einen Timer in Ihrer Anwendung, um regelmäßig die `playbackInformation` -Eigenschaft der `qosProvider` -Instanz. Die `playbackInformation` -Eigenschaft liefert eine Momentaufnahme der aktuellen Wiedergabestatistiken. Beispiel:

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```
