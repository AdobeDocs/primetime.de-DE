---
description: Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.
title: Medienressource mit MediaPlayerItemLoader laden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---


# Medienressource mit MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader} laden

Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.

Mithilfe der `MediaPlayerItemLoader`-Klasse können Sie eine Medienressource für die entsprechende `MediaPlayerItem`-Instanz austauschen, ohne eine Ansicht an eine `MediaPlayer`-Instanz anzuhängen, was zur Zuordnung der Videodekodierungs-Hardware-Ressourcen führen würde. Der Prozess zum Abrufen der `MediaPlayerItem`-Instanz ist asynchron.

1. Implementieren Sie Ereignis-Listener für diese `MediaPlayerItemLoader`-Ereignis:

   * `MediaPlayerItemLoaderEvent.ERROR` Ereignis

      TVSDK verwendet dies, um Ihre Anwendung darüber zu informieren, dass ein Fehler aufgetreten ist. TVSDK stellt eine Fehlereigenschaft bereit, die diagnostische Informationen enthält.

1. Registrieren Sie diese Instanz bei `MediaPlayerItemLoader`.
1. Rufen Sie `DefaultMediaPlayerItemLoader.load` auf und übergeben Sie eine Instanz eines `MediaResource`-Objekts.

   Die URL des Objekts `MediaResource` muss auf den Stream verweisen, für den Sie Informationen abrufen möchten. Beispiel:

   ```
   private function onLoadError(event:MediaPlayerItemLoaderEvent):void { 
       // something went wrong - look at the error code and description 
       // contained within the event.error 
   } 
   private function onLoadCompleted(event:MediaPlayerItemLoaderEvent):void { 
       // information is available - look at the data in the "event.item" object 
   } 
   // instantiate the MediaPlayerItemLoader object and register event listeners 
   var itemLoader:MediaPlayerItemLoader = new DefaultMediaPlayerItemLoader(); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.ERROR, onLoadError); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.COMPLETED, onLoadCompleted); 
   // create the MediaResource instance and set the URL to point to the actual media stream 
   var mediaResource:MediaResource = 
     MediaResource.createFromURL("https://example.com/media/test_media.m3u8", null); 
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```

