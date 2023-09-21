---
description: Sie können eine Stelle einrichten, an der Fehler verarbeitet werden.
title: Einrichten der Fehlerbehandlung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Einrichten der Fehlerbehandlung {#set-up-error-handling}

Sie können eine Stelle einrichten, an der Fehler verarbeitet werden.

1. Implementieren einer Ereignisrückruffunktion für `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK übergibt Ereignisinformationen, z. B. `MediaPlayerStatusChangeEvent` -Objekt.
1. Wenn im Callback der zurückgegebene Status `MediaPlayerStatus.ERROR`, stellen Sie eine Logik bereit, um alle Fehler zu verarbeiten.
1. Nachdem der Fehler verarbeitet wurde, setzen Sie die `MediaPlayer` -Objekt oder laden Sie eine neue Medienressource.

   Wenn die Variable `MediaPlayer` -Objekt befindet sich im Fehlerstatus und bleibt in diesem Status, bis Sie es mithilfe der `MediaPlayer.reset` -Methode.

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
