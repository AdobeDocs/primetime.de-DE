---
description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
seo-description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
seo-title: Laden einer Medienressource in den MediaPlayer
title: Laden einer Medienressource in den MediaPlayer
uuid: 8af3e8d1-359d-483c-b394-b95054f7265a
translation-type: tm+mt
source-git-commit: 84924d84bfa436a8807c2e8d74d1dc268d457051

---


# Laden einer Medienressource in den MediaPlayer{#load-a-media-resource-in-the-mediaplayer}

Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie das abspielbare Element Ihres `MediaPlayer` Objekts mit der neuen Ressource fest, die wiedergegeben werden soll.

   Ersetzen Sie das derzeit abspielbare Element Ihres MediaPlayer durch Aufruf `MediaPlayer.replaceCurrentResource` und Übergabe einer vorhandenen `MediaResource` Instanz.

1. Überprüfen Sie, ob mindestens die folgenden Änderungen vorliegen:

   * INITIALISIERT
   * VORBEREITT
   * FEHLER

      Über diese Ereignis kann das `MediaPlayer` Objekt Ihre Anwendung benachrichtigen, wenn die Medienressource erfolgreich geladen wurde.

1. Wenn der Status des Medienplayers auf INITIALIZED geändert wird, können Sie `MediaPlayer.prepareToPlay`

   Der Status INITIALIZED gibt an, dass das Medium erfolgreich geladen wurde. Das Aufrufen von `prepareToPlay` Beginn zur Auflösung und Platzierung der Werbung, falls vorhanden.

1. Wenn der Medienplayer-Status auf &quot;VORBEREITET&quot;geändert wird, wurde der Medienstream erfolgreich geladen und für die Wiedergabe vorbereitet.

   Wenn der Medienstream geladen wird, wird eine `MediaPlayerItem` erstellt.

Wenn ein Fehler auftritt, wechselt der MediaPlayer zum ERROR-Status. Außerdem benachrichtigt es Ihre Anwendung, indem es das `STATUS_CHANGED` Ereignis an Ihren `MediaPlayerStatusChangeEvent` Rückruf sendet.

Dadurch werden mehrere Parameter übergeben:
* Ein `type` Parameter des Typs Zeichenfolge mit dem Wert `ERROR`.

* Ein `MediaError` Parameter, mit dem Sie eine Benachrichtigung mit diagnostischen Informationen zum Ereignis &quot;error&quot;abrufen können.


<!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

Der folgende vereinfachte Beispielcode veranschaulicht den Vorgang zum Laden einer Medienressource:

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
