---
description: In der Adobe Primetime-Anzeigenentscheidung können Sie Anzeigen auf Schlüssel-Wert-Paare ausrichten.
title: Targeting-Informationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---

# Targeting-Informationen{#targeting-information}

In der Adobe Primetime-Anzeigenentscheidung können Sie Anzeigen auf Schlüssel-Wert-Paare ausrichten.

So übergeben Sie diese Schlüsselwertpaare an Browser TVSDK:

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```
