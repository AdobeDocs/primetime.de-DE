---
description: Ereignishandler ermöglichen es Browser TVSDK, auf Ereignisse zu reagieren.
title: Implementieren von Ereignis-Listenern und -Rückrufen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Implementieren von Ereignis-Listenern und -Rückrufen{#implement-event-listeners-and-callbacks}

Ereignishandler ermöglichen es Browser TVSDK, auf Ereignisse zu reagieren.

Wenn ein Ereignis eintritt, ruft der Ereignismechanismus des Browser TVSDK Ihren registrierten Ereignishandler auf und übergibt die Ereignisinformationen an den Handler.

Ihre Anwendung muss Ereignis-Listener für Browser TVSDK-Ereignisse implementieren, die sich auf Ihre Anwendung auswirken.

1. Bestimmen Sie, auf welche Ereignisse die Anwendung überwachen muss.

   * **Erforderliche Ereignisse**: Suchen Sie nach allen Wiedergabeereignissen.

     >[!IMPORTANT]
     >
     >Das Wiedergabeereignis `STATUS_CHANGED` stellt den Player-Status bereit, einschließlich Fehlern. Jeder Status kann sich auf den nächsten Schritt Ihres Players auswirken.

   * **Andere Ereignisse**: Optional, je nach Anwendung.

     Wenn Sie beispielsweise Werbung in Ihre Wiedergabe integrieren, sollten Sie alle `AdBreakPlaybackEvent` und `AdPlaybackEvent` -Ereignisse.

1. Implementieren Sie Ereignis-Listener für jedes Ereignis.

   Browser TVSDK gibt Parameterwerte an Ihre event-listener-Rückrufe zurück. Diese Werte enthalten relevante Informationen zum Ereignis, das Sie in Ihren Listenern verwenden können, um geeignete Aktionen durchzuführen.

   Beispiel:

   * Ereignistyp: `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Ereigniseigenschaft: `MediaPlayerStatus.<event>` verwendet wie folgt:

```js
player.addEventListener( 
            AdobePSDK.PSDKEventType.STATUS_CHANGED,  
            onStatusChange); 
 
onStatusChange = function (event) { 
 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.IDLE: 
            console.log("Player Status: IDLE"); 
            break;
```

1. Registrieren Sie Ihre Callback-Listener bei der `MediaPlayer` -Objekt mithilfe von `MediaPlayer.addEventListener`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
