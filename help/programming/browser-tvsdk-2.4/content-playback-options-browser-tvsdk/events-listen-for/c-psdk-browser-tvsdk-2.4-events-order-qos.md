---
description: Browser TVSDK sendet Servicequalitäts-Ereignis (QoS), um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der Servicestatistik beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.
seo-description: Browser TVSDK sendet Servicequalitäts-Ereignis (QoS), um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der Servicestatistik beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.
seo-title: QoS-Ereignis
title: QoS-Ereignis
uuid: 3384bc51-b435-4cd9-a1f8-9abf2605205b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '135'
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

