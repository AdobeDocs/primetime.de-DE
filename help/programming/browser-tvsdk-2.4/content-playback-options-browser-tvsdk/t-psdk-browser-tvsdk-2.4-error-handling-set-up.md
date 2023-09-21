---
description: Sie können eine Stelle in Ihrer Anwendung einrichten, um die Fehlerbehandlung als Reaktion auf den ERROR-Status durchzuführen.
title: Einrichten der Fehlerbehandlung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Einrichten der Fehlerbehandlung{#set-up-error-handling}

Sie können eine Stelle in Ihrer Anwendung einrichten, um die Fehlerbehandlung als Reaktion auf den ERROR-Status durchzuführen.

1. Hinzufügen eines Ereignis-Listeners für `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Beispiel:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. Wenn in Ihrem Ereignis-Listener die Variable `event.status` is `AdobePSDK.MediaPlayerStatus.ERROR`, stellen Sie die Logik zur Verarbeitung aller Fehler bereit.
1. Nachdem der Fehler verarbeitet wurde, setzen Sie die `MediaPlayer` -Objekt oder laden Sie eine neue Medienressource.

       Wenn sich das MediaPlayer-Objekt im FEHLER-Status befindet, kann es diesen Status erst beenden, nachdem Sie eine der folgenden Aufgaben ausgeführt haben:
   
   * Setzen Sie das MediaPlayer-Objekt mithilfe der `MediaPlayer.reset` -Methode.
   * Laden Sie eine neue Medienressource mithilfe der `MediaPlayer.replaceCurrentResource` -Methode.

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
