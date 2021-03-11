---
description: Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden.
title: Laden einer Medienressource in den MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---


# Medienressource im MediaPlayer {#load-a-media-resource-in-the-mediaplayer} laden

Laden Sie eine Ressource, indem Sie MediaResource direkt instanziieren und den wiederzugebenden Videoinhalt laden.

1. Legen Sie das abspielbare Element Ihres `MediaPlayer`-Objekts mit der neuen Ressource fest, die wiedergegeben werden soll.

   Ersetzen Sie das derzeit abspielbare Element des vorhandenen `MediaPlayer`-Objekts durch den Aufruf von `replaceCurrentResource` und die Übergabe einer vorhandenen `MediaResource`-Instanz.

1. Warten Sie, bis Browser TVSDK `AdobePSDK.MediaPlayerStatusChangeEvent` mit `event.status` auslöst, das einer der folgenden Werte entspricht:

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      Über diese Ereignis benachrichtigt das MediaPlayer-Objekt Ihre Anwendung, ob die Medienressource erfolgreich geladen wurde.

1. Wenn der Status des Medienplayers in `MediaPlayerStatus.INITIALIZED` geändert wird, können Sie `MediaPlayer.prepareToPlay` aufrufen.

   Der Status INITIALIZED gibt an, dass das Medium erfolgreich geladen wurde. Durch Aufruf von `prepareToPlay` werden die Auflösung und Platzierung der Werbung (sofern vorhanden) Beginn.
1. Wenn Browser TVSDK das `MediaPlayerStatus.PREPARED`-Ereignis auslöst, wurde der Medienstream erfolgreich geladen (ein MediaPlayerItem wird erstellt) und für die Wiedergabe vorbereitet.

Wenn ein Fehler auftritt, wechselt `MediaPlayer` zum `MediaPlayerStatus.ERROR`.

Sie benachrichtigt Ihre Anwendung auch, indem Sie das `MediaPlayerStatus.ERROR`-Ereignis auslöst.

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->


Der folgende vereinfachte Beispielcode veranschaulicht den Vorgang zum Laden einer Medienressource:

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
