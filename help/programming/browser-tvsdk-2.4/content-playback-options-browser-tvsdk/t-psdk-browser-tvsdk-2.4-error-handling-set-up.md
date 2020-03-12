---
description: Sie können eine Stelle in Ihrer Anwendung einrichten, an der die Fehlerverarbeitung als Reaktion auf den FEHLER-Status durchgeführt wird.
seo-description: Sie können eine Stelle in Ihrer Anwendung einrichten, an der die Fehlerverarbeitung als Reaktion auf den FEHLER-Status durchgeführt wird.
seo-title: Fehlerverarbeitung einrichten
title: Fehlerverarbeitung einrichten
uuid: 9e650ea7-86cb-4489-a3fd-80cd2ccef41f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Fehlerverarbeitung einrichten{#set-up-error-handling}

Sie können eine Stelle in Ihrer Anwendung einrichten, an der die Fehlerverarbeitung als Reaktion auf den FEHLER-Status durchgeführt wird.

1. Hinzufügen Ereignis-Listener für `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Beispiel:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. Geben Sie in Ihrem Ereignis-Listener die Logik für die Verarbeitung aller Fehler an, wenn der Wert `event.status` `AdobePSDK.MediaPlayerStatus.ERROR`ist.
1. Nachdem der Fehler verarbeitet wurde, setzen Sie das `MediaPlayer` Objekt zurück oder laden Sie eine neue Medienressource.

       Wenn sich das MediaPlayer-Objekt im ERROR-Status befindet, kann es diesen Status erst beenden, nachdem Sie eine der folgenden Aufgaben abgeschlossen haben:
   
   * Setzen Sie das MediaPlayer-Objekt mithilfe der `MediaPlayer.reset` Methode zurück.
   * Laden Sie eine neue Medienressource mit der `MediaPlayer.replaceCurrentResource` Methode.

<!--<a id="example_342CA5A8CD7C45BD88233C5BDBB17220"></a>-->

Beispiel:

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
onStatusChange = function (event) { 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.ERROR: 
            //handle error 
            break; 
    } 
} 
```

