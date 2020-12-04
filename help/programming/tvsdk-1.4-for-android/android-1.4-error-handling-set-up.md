---
description: Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.
seo-description: Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.
seo-title: Fehlerverarbeitung einrichten
title: Fehlerverarbeitung einrichten
uuid: a3182fce-85ac-4dad-bdb3-f9bfbdb2c62d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

---


# Einrichten der Fehlerverarbeitung{#set-up-error-handling}

Richten Sie eine zentrale Stelle ein, um Fehler zu verarbeiten.

1. Implementieren Sie eine Ereignis-Rückruffunktion für `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK übergibt Informationen zum Ereignis, z. B. ein `MediaPlayerStatusChangeEvent`-Objekt.
1. Geben Sie im Rückruf, wenn der zurückgegebene Status `MediaPlayerState.ERROR` ist, Logik an, um alle Fehler zu verarbeiten.
1. Nachdem der Fehler behandelt wurde, setzen Sie das `MediaPlayer`-Objekt zurück oder laden Sie eine neue Medienressource.

   Wenn sich das `MediaPlayer`-Objekt im Fehlerstatus befindet, bleibt es in diesem Status, bis Sie es mit der `MediaPlayer.reset`-Methode zurücksetzen.

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

Beispiel:

```java
mediaPlayer.addEventListener( 
  MediaPlayerEvent.STATUS_CHANGED, new StatusChangedEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
            // handle TVSDK error here 
        } 
    } 
});
```

