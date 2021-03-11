---
description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.
title: Laden einer Medienressource in den MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# Medienressource im MediaPlayer{#load-a-media-resource-in-the-mediaplayer} laden

Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden. Dies ist eine Möglichkeit, eine Medienressource zu laden.

1. Legen Sie das abspielbare Element Ihres `MediaPlayer`-Objekts mit der neuen Ressource fest, die wiedergegeben werden soll.

   Ersetzen Sie das derzeit abspielbare Element Ihres MediaPlayer durch den Aufruf von `MediaPlayer.replaceCurrentResource` und die Übergabe einer vorhandenen `MediaResource`-Instanz.

1. Überprüfen Sie, ob mindestens die folgenden Änderungen vorliegen:

   * INITIALISIERT
   * VORBEREITT
   * FEHLER

      Durch diese Ereignis kann das `MediaPlayer`-Objekt Ihre Anwendung benachrichtigen, wenn die Medienressource erfolgreich geladen wurde.

1. Wenn sich der Status des Medienplayers in INITIALIZED ändert, können Sie `MediaPlayer.prepareToPlay`

   Der Status INITIALIZED gibt an, dass das Medium erfolgreich geladen wurde. Durch Aufruf von `prepareToPlay` werden die Auflösung und Platzierung der Werbung (sofern vorhanden) Beginn.

1. Wenn der Medienplayer-Status auf &quot;VORBEREITET&quot;geändert wird, wurde der Medienstream erfolgreich geladen und für die Wiedergabe vorbereitet.

   Beim Laden des Medienstreams wird ein `MediaPlayerItem` erstellt.

Wenn ein Fehler auftritt, wechselt der MediaPlayer zum ERROR-Status. Sie benachrichtigt Ihre Anwendung auch, indem Sie das `STATUS_CHANGED`-Ereignis an Ihren `MediaPlayerStatusChangeEvent`-Rückruf senden.

Dadurch werden mehrere Parameter übergeben:
* Ein `type`-Parameter des Typs Zeichenfolge mit dem Wert `ERROR`.

* Ein `MediaError`-Parameter, mit dem Sie eine Benachrichtigung mit diagnostischen Informationen zum Ereignis &quot;error&quot;abrufen können.


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
