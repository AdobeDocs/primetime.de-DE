---
description: Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
title: Laden einer Medienressource im MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Laden einer Medienressource im MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie das abspielbare Element Ihres MediaPlayer mit der neuen Ressource fest, die wiedergegeben werden soll.

   Ersetzen Sie das derzeit abspielbare Element Ihres MediaPlayers durch einen Aufruf von `MediaPlayer.replaceCurrentItem` und Übergeben vorhandener `MediaResource` -Instanz.

1. Registrieren Sie eine Implementierung der `MediaPlayer.PlaybackEventListener` -Schnittstelle mit `MediaPlayer` -Instanz.

   * `onPrepared`
   * `onStateChanged`und suchen Sie nach INITIALIZED und FEHLER.

1. Wenn sich der Status des Medienplayers in INITIALISIERT ändert, können Sie `MediaPlayer.prepareToPlay`

   Der Status INITIALISIERT zeigt an, dass das Medium erfolgreich geladen wurde. Aufruf `prepareToPlay` startet den Prozess zur Auflösung und Platzierung der Werbung, falls vorhanden.

1. Wenn TVSDK die `onPrepared` -Rückruf, wurde der Medien-Stream erfolgreich geladen und für die Wiedergabe vorbereitet.

   Wenn der Medien-Stream geladen wird, wird ein `MediaPlayerItem` erstellt wird.

>Wenn ein Fehler auftritt, wird die `MediaPlayer` wechselt in den ERROR-Status. Sie benachrichtigt Ihre Anwendung auch, indem Sie Ihre `PlaybackEventListener.onStateChanged`Callback.
>
>Dadurch werden mehrere Parameter übergeben:
>* A `state` Parameter des Typs `MediaPlayer.PlayerState` mit dem Wert von `MediaPlayer.PlayerState.ERROR`.
>
>* A `notification` Parameter des Typs `MediaPlayerNotification` , die Diagnoseinformationen zum Fehlerereignis enthält.

Der folgende vereinfachte Beispielcode veranschaulicht den Ladevorgang einer Medienressource:

```java
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer  
instancemediaPlayer.addEventListener( 
  MediaPlayer.Event.PLAYBACK, 
  new MediaPlayer.PlaybackEventListener()) { 
    @Overridepublic void onPrepared() { 
        // at this point, the resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback 
        // once the resource is loaded, the MediaPlayer is able to 
        // provide a reference to the current "playable item" 
 
        MediaPlayerItem playerItem = mediaPlayer.CurrentItem(); 
 
        if (playerItem != null) {     
            // here we can take a look at the properties of the     
            // loaded stream 
        } 
    } @Overridepublic void onStateChanged( 
        MediaPlayer.PlayerState state,  
        MediaPlayerNotification notification) { 
        if (state == MediaPlayer.PlayerState.ERROR) { 
            // something bad happened - the resource cannot be loaded    
            // details about the problem are provided via the  
            // MediaPlayerNotification instance 
        }  
        elseif (state == MediaPlayer.PlayerState.INITIALIZED) {     
            mediaPlayer.prepareToPlay(); 
        } 
    } 
    // implementation of the other methods in the PlaybackEventListener interface... 
} 
```
