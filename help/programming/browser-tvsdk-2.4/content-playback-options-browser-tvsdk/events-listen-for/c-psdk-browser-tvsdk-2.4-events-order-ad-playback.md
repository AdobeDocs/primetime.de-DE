---
description: Wenn Ihre Wiedergabe Werbung enthält, sendet Browser TVSDK Ereignis/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.
title: Reihenfolge der Ereignis
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Reihenfolge der Ereignis für Werbung{#order-of-advertising-events}

Wenn Ihre Wiedergabe Werbung enthält, sendet Browser TVSDK Ereignis/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignis:

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* Für jede Anzeige in der Werbeunterbrechung werden die folgenden Meldungen ausgelöst:

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` (mehrere Male während der Wiedergabe einer Anzeige)
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

Das folgende Beispiel zeigt eine typische Progression von Ereignissen zur Anzeigenwiedergabe:

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```

