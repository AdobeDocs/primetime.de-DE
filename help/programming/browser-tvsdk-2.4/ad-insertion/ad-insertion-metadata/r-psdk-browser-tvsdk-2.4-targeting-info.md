---
description: Bei der Adobe Primetime-Anzeigenentscheidung können Sie Werbeanzeigen auf Schlüssel-Wert-Paare Zielgruppe werden.
seo-description: Bei der Adobe Primetime-Anzeigenentscheidung können Sie Werbeanzeigen auf Schlüssel-Wert-Paare Zielgruppe werden.
seo-title: Targeting-Informationen
title: Targeting-Informationen
uuid: 72114bef-36a1-4f2d-92e8-59f4885d70d2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '51'
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

