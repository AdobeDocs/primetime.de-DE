---
description: Browser TVSDK sendet Servicequalitäts-Ereignis (QoS), um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der Servicestatistik beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.
title: QoS-Ereignis
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---


# QoS-Ereignis{#qos-events}

Browser TVSDK sendet Servicequalitäts-Ereignis (QoS), um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der Servicestatistik beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.

Um über alle QoS-bezogenen Ereignis benachrichtigt zu werden, erstellen Sie eine Instanz von `AdobePSDK.QOSProvider` und fügen Sie die MediaPlayer-Instanz an diese `QOSProvider`-Instanz an:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Konfigurieren Sie einen Timer in Ihrer Anwendung, um die `playbackInformation`-Eigenschaft der `qosProvider`-Instanz regelmäßig zu überprüfen. Die `playbackInformation`-Eigenschaft stellt eine Momentaufnahme der aktuellen Wiedergabestatistik bereit. Beispiel:

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```

