---
description: Richten Sie eine zentrale Stelle ein, an der Fehler verarbeitet werden können.
title: Einrichten der Fehlerbehandlung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# Einrichten der Fehlerbehandlung{#set-up-error-handling}

Richten Sie eine zentrale Stelle ein, an der Fehler verarbeitet werden können.

1. Implementieren einer Ereignisrückruffunktion für `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK übergibt Ereignisinformationen, z. B. `MediaPlayerStatusChangeEvent` -Objekt.
1. Wenn im Callback der Status des Ereignisparameters `MediaPlayerStatus.ERROR`, stellen Sie eine Logik bereit, um alle Fehler zu verarbeiten.
1. Nachdem der Fehler verarbeitet wurde, setzen Sie die `MediaPlayer` -Objekt oder laden Sie eine neue Medienressource.

   Wenn die Variable `MediaPlayer` -Objekt befindet sich im ERROR-Status, kann diesen Status erst beenden, wenn Sie die `MediaPlayer` -Objekt (über die `MediaPlayer.reset` -Methode oder Laden einer neuen Medienressource ( `MediaPlayer.replaceCurrentItem`).

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
