---
description: Richten Sie eine zentrale Stelle ein, an der Fehler verarbeitet werden können.
title: Einrichten der Fehlerbehandlung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# Einrichten der Fehlerbehandlung{#set-up-error-handling}

Richten Sie eine zentrale Stelle ein, an der Fehler verarbeitet werden können.

1. Implementieren einer Ereignisrückruffunktion für `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK übergibt Ereignisinformationen, z. B. `MediaPlayerStatusChangeEvent` -Objekt.
1. Wenn im Callback der zurückgegebene Status `MediaPlayerState.ERROR`, stellen Sie eine Logik bereit, um alle Fehler zu verarbeiten.
1. Nachdem der Fehler verarbeitet wurde, setzen Sie die `MediaPlayer` -Objekt oder laden Sie eine neue Medienressource.

   Wenn die Variable `MediaPlayer` -Objekt befindet sich im Fehlerstatus und bleibt in diesem Status, bis Sie es mithilfe der `MediaPlayer.reset` -Methode.

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
