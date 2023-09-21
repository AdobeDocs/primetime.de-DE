---
description: Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
title: Laden einer Medienressource im Medienplayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Laden einer Medienressource im Medienplayer {#load-a-media-resource-in-the-media-player}

Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie den Medienplayer fest, um die neue Ressource wiederzugeben.

   Ersetzen Sie das derzeit abspielbare Element durch `MediaPlayer.replaceCurrentResource()` und Übergeben vorhandener `MediaResource` -Instanz.

   Dadurch wird der Ladevorgang der Ressource gestartet.

1. Registrieren `MediaPlayerEvent.STATUS_CHANGED` -Ereignis mit dem `MediaPlayer` -Instanz. Überprüfen Sie im Rückruf mindestens die folgenden Statuswerte:

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`

   Durch diese Ereignisse wird die `MediaPlayer` -Objekt benachrichtigt Ihre Anwendung, wenn sie die Medienressource erfolgreich geladen hat.
1. Wenn sich der Status des Medienplayers in `INITIALIZED`, können Sie `MediaPlayer.prepareToPlay()`.

   Dieser Status zeigt an, dass das Medium erfolgreich geladen wurde. Die neue `MediaPlayerItem` ist für die Wiedergabe bereit. Aufruf `prepareToPlay()` startet den Prozess zur Auflösung und Platzierung der Werbung, falls vorhanden.

Wenn ein Fehler auftritt, wechselt der Medienplayer zum `ERROR` -Status.

Der folgende vereinfachte Beispielcode veranschaulicht den Ladevorgang einer Medienressource:

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
