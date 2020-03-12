---
description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
seo-description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
seo-title: Laden einer Medienressource im Medienplayer
title: Laden einer Medienressource im Medienplayer
uuid: 1a27b83b-afa6-48c7-a701-e11b2d280810
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Laden einer Medienressource im Medienplayer {#load-a-media-resource-in-the-media-player}

Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie für den Medienplayer die Wiedergabe der neuen Ressource fest.

   Ersetzen Sie das derzeit abspielbare Element durch Aufrufen `MediaPlayer.replaceCurrentResource()` und Übergeben einer vorhandenen `MediaResource` Instanz.

   Dadurch wird der Ressourcenladevorgang Beginn.

1. Registrieren Sie das `MediaPlayerEvent.STATUS_CHANGED` Ereignis bei der `MediaPlayer` Instanz. Überprüfen Sie im Rückruf mindestens die folgenden Statuswerte:

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`
   Durch diese Ereignis benachrichtigt das `MediaPlayer` Objekt Ihre Anwendung, wenn die Medienressource erfolgreich geladen wurde.
1. Wenn der Status des Medienplayers geändert wird, können Sie `INITIALIZED`einen Aufruf ausführen `MediaPlayer.prepareToPlay()`.

   Dieser Status gibt an, dass das Medium erfolgreich geladen wurde. Die neue Version `MediaPlayerItem` kann wiedergegeben werden. Das Aufrufen von `prepareToPlay()` Beginn zur Auflösung und Platzierung der Werbung, falls vorhanden.

Wenn ein Fehler auftritt, wechselt der Medienplayer zum `ERROR` Status.

Der folgende vereinfachte Beispielcode veranschaulicht den Vorgang zum Laden einer Medienressource:

```java>
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatus status) { 
        if(event.getStatus() == MediaPlayerStatus.PREPARED) { 
            // The resource is successfully loaded and available. The  
            // MediaPlayer is ready to start the playback and can 
            // provide a reference to the current playable item 
            MediaPlayerItem playerItem = mediaPlayer.getCurrentItem(); 
            if (playerItem != null) { 
                // We can look at the properties of the loaded stream 
            } 
        } 
        else if (event.getStatus() == MediaPlayerStatus.ERROR) { 
            //Something bad happened - the resource cannot be loaded. 
            // The Metadata object in the event provides details. 
        } 
        else if (status == MediaPlayerStatus.INITIALIZED) { 
            mediaPlayer.prepareToPlay(); 
        } 
    } 
} 
```
