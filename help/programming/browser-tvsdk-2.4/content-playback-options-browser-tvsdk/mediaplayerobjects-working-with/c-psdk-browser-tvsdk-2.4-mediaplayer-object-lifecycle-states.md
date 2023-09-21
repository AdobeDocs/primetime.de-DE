---
description: Vom Zeitpunkt der Erstellung der MediaPlayer-Instanz bis zum Zeitpunkt ihrer Beendigung wird diese Instanz von einem Status zum nächsten übergegangen.
title: Lebenszyklus und Status des MediaPlayer-Objekts
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Lebenszyklus und Status des MediaPlayer-Objekts{#life-cycle-and-states-of-the-mediaplayer-object}

Vom Zeitpunkt der Erstellung der MediaPlayer-Instanz bis zum Zeitpunkt ihrer Beendigung wird diese Instanz von einem Status zum nächsten übergegangen.

Folgende Status sind möglich:

* **IDLE**: `MediaPlayerStatus.IDLE`

* **INITIALISIERUNG**: `MediaPlayerStatus.INITIALIZING`

* **INITIALISIERT**: `MediaPlayerStatus.INITIALIZED`

* **VORBEREITUNG**: `MediaPlayerStatus.PREPARING`

* **VORBEREITET**: `MediaPlayerStatus.PREPARED`

* **PLAYING**: `MediaPlayerStatus.PLAYING`

* **PAUSED**: `MediaPlayerStatus.PAUSED`

* **SUCHEN**: `MediaPlayerStatus.SEEKING`

* **COMPLETE**: `MediaPlayerStatus.COMPLETE`

* **FEHLER**: `MediaPlayerStatus.ERROR`

* **VERÖFFENTLICHT**: `MediaPlayerStatus.RELEASED`

Die vollständige Liste der Status wird unter `MediaPlayerStatus`.

Es ist nützlich, den Status des Players zu kennen, da einige Vorgänge nur zulässig sind, während sich der Player in einem bestimmten Status befindet. Beispiel: `play` kann nicht aufgerufen werden, während sie sich im IDLE-Status befinden. Sie muss aufgerufen werden, nachdem der Status VORBEREITET erreicht wurde. Der FEHLER-Status ändert auch, was als Nächstes passieren kann.

Wenn eine Medienressource geladen und wiedergegeben wird, wechselt der Player wie folgt:

1. Der Anfangsstatus lautet IDLE.
1. Ihre App-Aufrufe `MediaPlayer.replaceCurrentResource`, wodurch der Player in den Status INITIALISIEREN wechselt.
1. Wenn Browser TVSDK die Ressource erfolgreich lädt, ändert sich der Status in INITIALISIERT.
1. Ihre App-Aufrufe `MediaPlayer.prepareToPlay`und der Status in VORBEREITUNG geändert wird.
1. Browser TVSDK bereitet den Medien-Stream vor und startet die Auflösung der Anzeige und das Einfügen der Anzeige (sofern aktiviert).

   Wenn dieser Schritt abgeschlossen ist, werden Anzeigen in die Timeline eingefügt oder die Anzeigenverarbeitung ist fehlgeschlagen, und der Player-Status ändert sich in VORBEREITT.
1. Während Ihre Anwendung die Medien wiedergibt und anhält, wechselt der Status zwischen PLAYING und PAUSED.

   >[!TIP]
   >
   >Wenn Sie während der Wiedergabe oder Pause navigieren, das Gerät herunterfahren oder Anwendungen wechseln, ändert sich der Status in AUSGESETZT und die Ressourcen werden freigegeben. Um fortzufahren, stellen Sie den Medienplayer wieder her.

1. Wenn der Player das Ende des Streams erreicht, wird der Status ABGESCHLOSSEN.
1. Wenn Ihre Anwendung den Medienplayer veröffentlicht, ändert sich der Status in VERÖFFENTLICHT.
1. Wenn während des Prozesses ein Fehler auftritt, ändert sich der Status in ERROR.

Hier finden Sie eine Abbildung des Lebenszyklus einer MediaPlayer-Instanz:

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

Sie können den Status verwenden, um dem Benutzer Feedback zum Prozess zu geben (z. B. ein Spinner beim Warten auf die nächste Statusänderung) oder die nächsten Schritte beim Abspielen der Medien durchzuführen, z. B. auf den entsprechenden Status zu warten, bevor die nächste Methode aufgerufen wird.

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
