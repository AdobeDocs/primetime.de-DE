---
description: Ereignis-Handler ermöglichen es Browser TVSDK, auf Ereignis zu reagieren.
seo-description: Ereignis-Handler ermöglichen es Browser TVSDK, auf Ereignis zu reagieren.
seo-title: Implementieren von Ereignis-Listenern und -Rückrufen
title: Implementieren von Ereignis-Listenern und -Rückrufen
uuid: 63f62c60-505e-4f83-bc0d-58895d85a75a
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 1%

---


# Implementieren von Ereignis-Listenern und -Rückrufen{#implement-event-listeners-and-callbacks}

Ereignis-Handler ermöglichen es Browser TVSDK, auf Ereignis zu reagieren.

Wenn ein Ereignis auftritt, ruft der Ereignis-Mechanismus von Browser TVSDK Ihren registrierten Ereignis-Handler auf und leitet die Ereignis-Informationen an den Handler weiter.

Ihre Anwendung muss Ereignis-Listener für Browser TVSDK-Ereignis implementieren, die Ihre Anwendung betreffen.

1. Bestimmen Sie, auf welche Ereignis Ihre Anwendung hören muss.

   * **Erforderliche Ereignis**: Suchen Sie nach allen Ereignissen für die Wiedergabe.

      >[!IMPORTANT]
      >
      >Das play-Ereignis `STATUS_CHANGED` stellt den Player-Status einschließlich Fehler bereit. Jeder Status kann sich auf den nächsten Schritt Ihres Spielers auswirken.

   * **Andere Ereignisse**: Optional, je nach Anwendung.

      Wenn Sie z. B. Werbung in Ihre Wiedergabe integrieren, sollten Sie alle `AdBreakPlaybackEvent`- und `AdPlaybackEvent`-Ereignis abhören.

1. Implementieren Sie Ereignis-Listener für jedes Ereignis.

   Browser TVSDK gibt Parameterwerte an Ihre Ereignis-Listener-Rückrufe zurück. Diese Werte liefern relevante Informationen über das Ereignis, das Sie in Ihren Listenern verwenden können, um entsprechende Aktionen durchzuführen.

   Beispiel:

   * Ereignistyp: `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Ereignis-Eigenschaft: `MediaPlayerStatus.<event>` wird wie folgt verwendet:

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

1. Registrieren Sie Ihre Callback-Listener mit dem `MediaPlayer`-Objekt, indem Sie `MediaPlayer.addEventListener` verwenden.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
