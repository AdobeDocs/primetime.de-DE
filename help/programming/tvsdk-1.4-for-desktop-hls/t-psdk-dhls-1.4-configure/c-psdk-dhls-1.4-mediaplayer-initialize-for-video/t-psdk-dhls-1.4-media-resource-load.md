---
description: Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
title: Laden einer Medienressource im MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Laden einer Medienressource im MediaPlayer{#load-a-media-resource-in-the-mediaplayer}

Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie Ihre `MediaPlayer` des abspielbaren Elements des Objekts mit der neuen Ressource, die wiedergegeben werden soll.

   Ersetzen Sie das derzeit abspielbare Element Ihres MediaPlayers durch einen Aufruf von `MediaPlayer.replaceCurrentResource` und Übergeben vorhandener `MediaResource` -Instanz.

1. Suchen Sie nach mindestens den folgenden Änderungen:

   * INITIALISIERT
   * VORBEREITET
   * FEHLER

     Durch diese Ereignisse wird die `MediaPlayer` -Objekt kann Ihre Anwendung benachrichtigen, wenn die Medienressource erfolgreich geladen wurde.

1. Wenn sich der Status des Medienplayers in INITIALISIERT ändert, können Sie `MediaPlayer.prepareToPlay`

   Der Status INITIALISIERT zeigt an, dass das Medium erfolgreich geladen wurde. Aufruf `prepareToPlay` startet den Prozess zur Auflösung und Platzierung der Werbung, falls vorhanden.

1. Wenn sich der Medienplayer-Status in VORBEREITT ändert, wurde der Medien-Stream erfolgreich geladen und ist für die Wiedergabe vorbereitet.

   Wenn der Medien-Stream geladen wird, wird ein `MediaPlayerItem` erstellt wird.

Wenn ein Fehler auftritt, wechselt der MediaPlayer zum ERROR-Status. Außerdem wird Ihre Anwendung benachrichtigt, indem die `STATUS_CHANGED` -Ereignis zu Ihrer `MediaPlayerStatusChangeEvent` Callback.

Dadurch werden mehrere Parameter übergeben:
* A `type` Parameter des Typs Zeichenfolge mit dem Wert `ERROR`.

* A `MediaError` -Parameter, mit dem Sie eine Benachrichtigung mit Diagnoseinformationen zum Fehlerereignis abrufen können.


<!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

Der folgende vereinfachte Beispielcode veranschaulicht den Ladevorgang einer Medienressource:

```
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register an event listener with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
   switch(event.status) { 
      case MediaPlayerStatus.INITIALIZED: 
          // at this point, the resource is successfully loaded 
          // the media player will provide a reference to the current 
          // "playable item" ( is guarantee to be valid and not-null). 
          var playerItem: MediaPlayerItem = mediaPlayer.currentItem; 
          // we can take a look at the media item characteristics like 
          // alternate audio tracks, profile information, if is a live stream 
          // if is drm protected 
          mediaPlayer.prepareToPlay(); 
          break; 
    case MediaPlayerStatus.PREPARED: 
         // at this point, the resource is successfully processed all  
         // advertisement placements have been executed and the the  
         // MediaPlayer is ready to start the playback 
        if (autoPlay) { 
            mediaPlayer.play(); 
        } 
        break; 
    case MediaPlayerStatus.ERROR: 
        // something bad happened - the resource cannot be loaded 
        // details about the problem are provided via the event.error property 
        break; 
        // implementation of the other methods in the PlaybackEventListener interface 
        ... 
    } 
}
```
