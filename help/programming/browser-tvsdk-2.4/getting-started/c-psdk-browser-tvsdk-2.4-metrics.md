---
description: Browser TVSDK stellt Metriken zum Analysieren und Debuggen bereit. Sie können diese Metriken mit QoSProvider abrufen.
seo-description: Browser TVSDK stellt Metriken zum Analysieren und Debuggen bereit. Sie können diese Metriken mit QoSProvider abrufen.
seo-title: Metriken
title: Metriken
uuid: 4734e532-1f83-4691-b1bd-785f78e55d8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Metriken{#metrics}

Browser TVSDK stellt Metriken zum Analysieren und Debuggen bereit. Sie können diese Metriken mit QoSProvider abrufen.

Beispiel:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

