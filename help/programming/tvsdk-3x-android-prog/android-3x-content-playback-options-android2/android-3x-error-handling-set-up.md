---
description: Sie können eine Stelle einrichten, an der Fehler behandelt werden.
title: Fehlerverarbeitung einrichten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 2%

---


# Einrichten der Fehlerverarbeitung {#set-up-error-handling}

Sie können eine Stelle einrichten, an der Fehler behandelt werden.

1. Implementieren Sie eine Ereignis-Rückruffunktion für `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK übergibt Informationen zum Ereignis, z. B. ein `MediaPlayerStatusChangeEvent`-Objekt.
1. Wenn der zurückgegebene Status im Rückruf `MediaPlayerStatus.ERROR` lautet, geben Sie eine Logik zur Verarbeitung aller Fehler ein.
1. Nachdem der Fehler behandelt wurde, setzen Sie das `MediaPlayer`-Objekt zurück oder laden Sie eine neue Medienressource.

   Wenn sich das `MediaPlayer`-Objekt im Fehlerstatus befindet, bleibt es in diesem Status, bis Sie es mit der `MediaPlayer.reset`-Methode zurücksetzen.

<!--<a id="example_E74BB605ED08450295B8902F1E4BB8F5"></a>-->

Beispiel:

```java
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
        // handle TVSDK error here 
        } 
    } 
});
```
