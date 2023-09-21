---
description: Browser TVSDK bietet Metriken zur Analyse und zum Debugging. Sie können diese Metriken mit QoSProvider abrufen.
title: Metriken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# Metriken{#metrics}

Browser TVSDK bietet Metriken zur Analyse und zum Debugging. Sie können diese Metriken mit QoSProvider abrufen.

Beispiel:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```
