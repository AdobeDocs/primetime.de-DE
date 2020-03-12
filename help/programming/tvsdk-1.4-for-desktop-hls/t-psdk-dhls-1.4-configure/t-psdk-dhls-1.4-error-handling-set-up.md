---
description: Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.
seo-description: Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.
seo-title: Fehlerverarbeitung einrichten
title: Fehlerverarbeitung einrichten
uuid: ff56180d-aa74-4b7c-a24c-e536d874c2e6
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Fehlerverarbeitung einrichten{#set-up-error-handling}

Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.

1. Implementieren Sie eine Ereignis-Rückruffunktion für `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK übergibt Informationen zum Ereignis, z. B. ein `MediaPlayerStatusChangeEvent` Objekt.
1. Wenn der Status des Ereignis-Parameters im Rückruf `MediaPlayerStatus.ERROR`ist, geben Sie eine Logik zur Verarbeitung aller Fehler an.
1. Nachdem der Fehler verarbeitet wurde, setzen Sie das `MediaPlayer` Objekt zurück oder laden Sie eine neue Medienressource.

   Wenn sich das `MediaPlayer` Objekt im FEHLER-Status befindet, kann es diesen Status erst dann beenden, wenn Sie das `MediaPlayer` Objekt zurücksetzen (über die `MediaPlayer.reset` Methode) oder eine neue Medienressource laden ( `MediaPlayer.replaceCurrentItem`).

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

Beispiel:

```
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
 
private void onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    if (event.status == MediaPlayerStatus.ERROR) { 
        var error:MediaError = event.error; 
        // handle TVSDK error here 
    } 
} 
```

