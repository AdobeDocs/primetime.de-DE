---
description: Browser TVSDK stellt Metriken zum Analysieren und Debuggen bereit. Sie können diese Metriken mit QoSProvider abrufen.
title: Metriken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 5%

---


# Metriken{#metrics}

Browser TVSDK stellt Metriken zum Analysieren und Debuggen bereit. Sie können diese Metriken mit QoSProvider abrufen.

Beispiel:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

