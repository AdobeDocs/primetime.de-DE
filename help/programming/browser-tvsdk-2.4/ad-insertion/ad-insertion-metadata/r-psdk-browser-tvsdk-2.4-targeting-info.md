---
description: Bei der Adobe Primetime-Anzeigenentscheidung können Sie Werbeanzeigen auf Schlüssel-Wert-Paare Zielgruppe werden.
title: Targeting-Informationen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# Targeting-Informationen{#targeting-information}

Bei der Adobe Primetime-Anzeigenentscheidung können Sie Werbeanzeigen auf Schlüssel-Wert-Paare Zielgruppe werden.

So übergeben Sie diese Schlüsselwertpaare an Browser TVSDK:

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```

