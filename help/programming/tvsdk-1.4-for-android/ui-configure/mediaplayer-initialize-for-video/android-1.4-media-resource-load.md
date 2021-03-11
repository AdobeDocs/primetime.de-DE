---
description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
title: Laden einer Medienressource in den MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Medienressource im MediaPlayer {#load-a-media-resource-in-the-mediaplayer} laden

Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie das abspielbare Element Ihres MediaPlayer mit der neuen Ressource fest, die wiedergegeben werden soll.

   Ersetzen Sie das derzeit abspielbare Element Ihres MediaPlayer durch den Aufruf von `MediaPlayer.replaceCurrentItem` und die Übergabe einer vorhandenen `MediaResource`-Instanz.

1. Registrieren Sie eine Implementierung der `MediaPlayer.PlaybackEventListener`-Schnittstelle mit der `MediaPlayer`-Instanz.

   * `onPrepared`
   * `onStateChanged`und suchen Sie nach INITIALIZED und FEHLER.

1. Wenn sich der Status des Medienplayers in INITIALIZED ändert, können Sie `MediaPlayer.prepareToPlay`

   Der Status INITIALIZED gibt an, dass das Medium erfolgreich geladen wurde. Durch Aufruf von `prepareToPlay` werden die Auflösung und Platzierung der Werbung (sofern vorhanden) Beginn.

1. Wenn TVSDK den Rückruf `onPrepared` aufruft, wurde der Medienstream erfolgreich geladen und für die Wiedergabe vorbereitet.

   Beim Laden des Medienstreams wird ein `MediaPlayerItem` erstellt.

>Tritt ein Fehler auf, wechselt `MediaPlayer` zum ERROR-Status. Sie benachrichtigt Ihre Anwendung auch über Ihren `PlaybackEventListener.onStateChanged`Rückruf.
>
>Dadurch werden mehrere Parameter übergeben:
>* Ein `state`-Parameter des Typs `MediaPlayer.PlayerState` mit dem Wert `MediaPlayer.PlayerState.ERROR`.
   >
   >
* Ein `notification`-Parameter des Typs `MediaPlayerNotification`, der diagnostische Informationen zum Ereignis &quot;error&quot;enthält.


Der folgende vereinfachte Beispielcode veranschaulicht den Vorgang zum Laden einer Medienressource:

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
