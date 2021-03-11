---
description: Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.
title: Fehlerverarbeitung einrichten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 2%

---


# Einrichten der Fehlerverarbeitung{#set-up-error-handling}

Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.

1. Implementieren Sie eine Ereignis-Rückruffunktion für `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK übergibt Informationen zum Ereignis, z. B. ein `MediaPlayerStatusChangeEvent`-Objekt.
1. Geben Sie im Rückruf eine Logik an, wenn der Ereignis-Parameter `MediaPlayerStatus.ERROR` lautet.
1. Nachdem der Fehler behandelt wurde, setzen Sie das `MediaPlayer`-Objekt zurück oder laden Sie eine neue Medienressource.

   Wenn sich das `MediaPlayer`-Objekt im ERROR-Status befindet, kann es diesen Status erst dann beenden, wenn Sie entweder das `MediaPlayer`-Objekt zurücksetzen (über die `MediaPlayer.reset`-Methode) oder eine neue Medienressource ( `MediaPlayer.replaceCurrentItem`) laden.

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

