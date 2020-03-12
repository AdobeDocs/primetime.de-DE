---
description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
seo-description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
seo-title: Laden einer Medienressource in den MediaPlayer
title: Laden einer Medienressource in den MediaPlayer
uuid: 6ee8032f-0728-423f-a1d2-5030aa7db14f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Laden einer Medienressource in den MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie das abspielbare Element Ihres MediaPlayer mit der neuen Ressource fest, die wiedergegeben werden soll.

   Ersetzen Sie das derzeit abspielbare Element Ihres MediaPlayer durch Aufruf `MediaPlayer.replaceCurrentItem` und Übergabe einer vorhandenen `MediaResource` Instanz.

1. Registrieren Sie eine Implementierung der `MediaPlayer.PlaybackEventListener` Schnittstelle mit der `MediaPlayer` Instanz.

   * `onPrepared`
   * `onStateChanged`und suchen Sie nach INITIALIZED und FEHLER.

1. Wenn der Status des Medienplayers auf INITIALIZED geändert wird, können Sie `MediaPlayer.prepareToPlay`

   Der Status INITIALIZED gibt an, dass das Medium erfolgreich geladen wurde. Das Aufrufen von `prepareToPlay` Beginn zur Auflösung und Platzierung der Werbung, falls vorhanden.
1. Wenn TVSDK den `onPrepared` Rückruf aufruft, wurde der Medienstream erfolgreich geladen und für die Wiedergabe vorbereitet.

   Wenn der Medienstream geladen wird, wird eine `MediaPlayerItem` erstellt.
>Tritt ein Fehler auf, wechselt der `MediaPlayer` Status &quot;ERROR&quot;. Sie benachrichtigt Ihre Anwendung auch durch Aufruf Ihres `PlaybackEventListener.onStateChanged`Rückrufs.
>
>Dadurch werden mehrere Parameter übergeben: >
>* Ein `state` Parameter vom Typ `MediaPlayer.PlayerState` mit dem Wert `MediaPlayer.PlayerState.ERROR`.
   >
   >
* Ein `notification` Typparameter, `MediaPlayerNotification` der diagnostische Informationen zum Ereignis &quot;error&quot;enthält.


Der folgende vereinfachte Beispielcode veranschaulicht den Vorgang zum Laden einer Medienressource:

>```java>
>// mediaResource is a properly configured MediaResource instance 
>// mediaPlayer is a MediaPlayer instance 
>// register a PlaybackEventListener implementation with the MediaPlayer  
>instancemediaPlayer.addEventListener( 
>   MediaPlayer.Event.PLAYBACK, 
>   new MediaPlayer.PlaybackEventListener()) { 
>       @Overridepublic void onPrepared() { 
>               // at this point, the resource is successfully loaded and available 
>               // and the MediaPlayer is ready to start the playback 
>               // once the resource is loaded, the MediaPlayer is able to 
>               // provide a reference to the current "playable item" 
> 
>        
       MediaPlayerItem playerItem = mediaPlayer.CurrentItem(); 
> 
>        
       if (playerItem != null) {     
>                       // here we can take a look at the properties of the     
>                       // loaded stream 
>               } 
>       } @Overridepublic void onStateChanged( 
>               MediaPlayer.PlayerState state,  
>               MediaPlayerNotification notification) { 
>               if (state == MediaPlayer.PlayerState.ERROR) { 
>                       // something bad happened - the resource cannot be loaded    
>                       // details about the problem are provided via the  
>                       // MediaPlayerNotification instance 
>               }  
>               elseif (state == MediaPlayer.PlayerState.INITIALIZED) {     
>                       mediaPlayer.prepareToPlay(); 
>               } 
>       } 
>       // implementation of the other methods in the PlaybackEventListener interface... 
>} 
>
>
```>


