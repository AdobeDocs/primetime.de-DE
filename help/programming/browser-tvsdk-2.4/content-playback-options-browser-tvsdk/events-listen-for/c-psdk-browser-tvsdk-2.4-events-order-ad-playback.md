---
description: Wenn Ihre Wiedergabe Werbung enthält, sendet Browser TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen in der erwarteten Sequenz implementieren.
title: Reihenfolge von Werbeintereignissen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Reihenfolge von Werbeintereignissen{#order-of-advertising-events}

Wenn Ihre Wiedergabe Werbung enthält, sendet Browser TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen in der erwarteten Sequenz implementieren.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignisse:

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* Folgendes wird für jede Anzeige in der Werbeunterbrechung gesendet:

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` (mehrmals während der Wiedergabe einer Anzeige)
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

Das folgende Beispiel zeigt eine typische Progression von Anzeigenwiedergabeereignissen:

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```
