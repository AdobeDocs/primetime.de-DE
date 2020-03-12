---
description: Sie können eine Stelle einrichten, an der Fehler verarbeitet werden.
seo-description: Sie können eine Stelle einrichten, an der Fehler verarbeitet werden.
seo-title: Fehlerverarbeitung einrichten
title: Fehlerverarbeitung einrichten
uuid: fde47fa5-5ca5-4be5-a7e7-3227c5e4c670
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Fehlerverarbeitung einrichten {#set-up-error-handling}

Sie können eine Stelle einrichten, an der Fehler verarbeitet werden.

1. Implementieren Sie eine Ereignis-Rückruffunktion für `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK übergibt Informationen zum Ereignis, z. B. ein `MediaPlayerStatusChangeEvent` Objekt.
1. Geben Sie im Rückruf, wenn der zurückgegebene Status `MediaPlayerStatus.ERROR`ist, eine Logik zur Verarbeitung aller Fehler ein.
1. Nachdem der Fehler verarbeitet wurde, setzen Sie das `MediaPlayer` Objekt zurück oder laden Sie eine neue Medienressource.

   Wenn sich das `MediaPlayer` Objekt im Fehlerstatus befindet, bleibt es in diesem Status, bis Sie es mithilfe der `MediaPlayer.reset` Methode zurücksetzen.

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

