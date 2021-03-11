---
description: Sie können eine Stelle in Ihrer Anwendung einrichten, an der die Fehlerverarbeitung als Reaktion auf den FEHLER-Status durchgeführt wird.
title: Fehlerverarbeitung einrichten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 3%

---


# Einrichten der Fehlerverarbeitung{#set-up-error-handling}

Sie können eine Stelle in Ihrer Anwendung einrichten, an der die Fehlerverarbeitung als Reaktion auf den FEHLER-Status durchgeführt wird.

1. hinzufügen eines Ereignis-Listeners für `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Beispiel:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. Wenn `event.status` in Ihrem Ereignis-Listener `AdobePSDK.MediaPlayerStatus.ERROR`  ist, geben Sie die Logik an, um alle Fehler zu verarbeiten.
1. Nachdem der Fehler behandelt wurde, setzen Sie das `MediaPlayer`-Objekt zurück oder laden Sie eine neue Medienressource.

       Wenn sich das MediaPlayer-Objekt im ERROR-Status befindet, kann es diesen Status erst beenden, nachdem Sie eine der folgenden Aufgaben abgeschlossen haben:
   
   * Setzen Sie das MediaPlayer-Objekt mit der `MediaPlayer.reset`-Methode zurück.
   * Laden Sie eine neue Medienressource mit der `MediaPlayer.replaceCurrentResource`-Methode.

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

