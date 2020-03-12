---
description: Diese Instanz wird von dem Zeitpunkt an, zu dem die MediaPlayer-Instanz erstellt wurde, bis zu dem Zeitpunkt, zu dem sie beendet wird, von einem Status zum nächsten Transition.
seo-description: Diese Instanz wird von dem Zeitpunkt an, zu dem die MediaPlayer-Instanz erstellt wurde, bis zu dem Zeitpunkt, zu dem sie beendet wird, von einem Status zum nächsten Transition.
seo-title: Lebenszyklus und Status des MediaPlayer-Objekts
title: Lebenszyklus und Status des MediaPlayer-Objekts
uuid: fe76ea80-aaa8-43bc-9b81-85e0551f70dd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Lebenszyklus und Status des MediaPlayer-Objekts{#life-cycle-and-states-of-the-mediaplayer-object}

Diese Instanz wird von dem Zeitpunkt an, zu dem die MediaPlayer-Instanz erstellt wurde, bis zu dem Zeitpunkt, zu dem sie beendet wird, von einem Status zum nächsten Transition.

Die folgenden Statusangaben sind möglich:

* **IDLE**: `MediaPlayerStatus.IDLE`

* **INITIALISIERUNG**: `MediaPlayerStatus.INITIALIZING`

* **INITIALISIERT**: `MediaPlayerStatus.INITIALIZED`

* **VORBEREITUNG**: `MediaPlayerStatus.PREPARING`

* **VORBEREITET**: `MediaPlayerStatus.PREPARED`

* **ABSPIELEN**: `MediaPlayerStatus.PLAYING`

* **ANGEHALTEN**: `MediaPlayerStatus.PAUSED`

* **SUCHEN**: `MediaPlayerStatus.SEEKING`

* **ABGESCHLOSSEN**: `MediaPlayerStatus.COMPLETE`

* **FEHLER**: `MediaPlayerStatus.ERROR`

* **VERÖFFENTLICHT**: `MediaPlayerStatus.RELEASED`

Die vollständige Liste der Statusangaben wird in `MediaPlayerStatus`definiert.

Es ist nützlich, den Status des Players zu kennen, da einige Operationen nur zulässig sind, wenn der Player sich in einem bestimmten Status befindet. Beispielsweise `play` kann während des IDLE-Status nicht aufgerufen werden. Sie muss aufgerufen werden, nachdem der Status &quot;VORBEREITT&quot;erreicht wurde. Der FEHLER-Status ändert auch, was als Nächstes passieren kann.

Beim Laden und Abspielen einer Medienressource wird der Player wie folgt Transition:

1. Der Ausgangszustand ist IDLE.
1. Ihre Anwendung ruft `MediaPlayer.replaceCurrentResource`auf, wodurch der Player in den Status INITIALIZING wechselt.
1. Wenn Browser TVSDK die Ressource erfolgreich lädt, ändert sich der Status in INITIALIZED.
1. Ihre Anwendung ruft `MediaPlayer.prepareToPlay`auf und der Status wechselt zu &quot;VORBEREITEN&quot;.
1. Browser TVSDK bereitet den Medienstream vor und Beginn die Auflösung und das Einfügen der Anzeige (sofern aktiviert).

   Wenn dieser Schritt abgeschlossen ist, werden Anzeigen in die Zeitleiste eingefügt oder der Anzeigenvorgang ist fehlgeschlagen, und der Player-Status ändert sich in &quot;VORBEREITET&quot;.
1. Während Ihre Anwendung die Medien wiedergibt und anhält, wechselt der Status zwischen PLAYING und PAUSED.

   >[!TIP]
   >
   >Wenn Sie während der Wiedergabe oder beim Anhalten der Wiedergabe weg von der Wiedergabe navigieren, das Gerät herunterfahren oder die Anwendung wechseln, wird der Status auf AUSGESETZT geändert und Ressourcen werden freigegeben. Um fortzufahren, stellen Sie den Medienplayer wieder her.

1. Wenn der Player das Ende des Streams erreicht, wird der Status ABGESCHLOSSEN.
1. Wenn Ihre Anwendung den Medienplayer veröffentlicht, ändert sich der Status in RELEASED.
1. Tritt während des Prozesses ein Fehler auf, ändert sich der Status in ERROR.

Hier ist eine Abbildung des Lebenszyklus einer MediaPlayer-Instanz:

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

Sie können den Status verwenden, um dem Benutzer Feedback zum Prozess zu geben (z. B. ein Kreisel, während er auf die nächste Statusänderung wartet) oder um die nächsten Schritte beim Abspielen des Mediums zu unternehmen, z. B. auf den entsprechenden Status zu warten, bevor die nächste Methode aufgerufen wird.

Beispiel:

```js
function onStateChanged(state) { 
    switch(state) { 
        // It is recommended that you call prepareToPlay()  
        // after receiving the INITIALIZED state             
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            mediaPlayer.prepareToPlay(); 
            break; 
    } 
} 
```

