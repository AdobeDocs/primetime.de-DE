---
description: Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden.
title: Laden einer Medienressource im MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Laden einer Medienressource im MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laden Sie eine Ressource, indem Sie eine MediaResource direkt instanziieren und den abzuspielenden Videoinhalt laden.

1. Legen Sie Ihre `MediaPlayer` des abspielbaren Elements des Objekts mit der neuen Ressource, die wiedergegeben werden soll.

   Vorhandene ersetzen `MediaPlayer` Das derzeit abspielbare Objekt des Objekts durch Aufruf von `replaceCurrentResource` und Übergeben vorhandener `MediaResource` -Instanz.

1. Warten Sie, bis Browser TVSDK gesendet wird `AdobePSDK.MediaPlayerStatusChangeEvent` mit `event.status` der einem der folgenden Werte entspricht:

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

     Durch diese Ereignisse benachrichtigt das MediaPlayer-Objekt Ihre Anwendung, ob die Medienressource erfolgreich geladen wurde.

1. Wenn sich der Status des Medienplayers in `MediaPlayerStatus.INITIALIZED`, können Sie `MediaPlayer.prepareToPlay`.

   Der Status INITIALISIERT zeigt an, dass das Medium erfolgreich geladen wurde. Aufruf `prepareToPlay` startet den Prozess zur Auflösung und Platzierung der Werbung, falls vorhanden.
1. Wenn Browser TVSDK die `MediaPlayerStatus.PREPARED` -Ereignis, wenn der Medien-Stream erfolgreich geladen wurde (ein MediaPlayerItem erstellt wurde) und für die Wiedergabe vorbereitet ist.

Wenn ein Fehler auftritt, wird die `MediaPlayer` wechselt zu `MediaPlayerStatus.ERROR`.

Außerdem wird Ihre Anwendung benachrichtigt, indem die `MediaPlayerStatus.ERROR` -Ereignis.

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

Der folgende vereinfachte Beispielcode veranschaulicht den Ladevorgang einer Medienressource:

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                        onStatusChange); 
 
onStatusChange = function (event) { 
    var msg = ""; 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            msg = "Player Status: INITIALIZED"; 
            console.log(msg); 
            player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARED: 
        // The resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback. 
        // Once the resource is loaded, the MediaPlayer can 
        // provide a reference to the current "playable item" 
           MediaPlayerItem playerItem = player.currentItem; 
           if (playerItem != null) {  
              // here we can look at the properties of the  
              // loadedstream 
           } 
           break; 
    } 
}
```
