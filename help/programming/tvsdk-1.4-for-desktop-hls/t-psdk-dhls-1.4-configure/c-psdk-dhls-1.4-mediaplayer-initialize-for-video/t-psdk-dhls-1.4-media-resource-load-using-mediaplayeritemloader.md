---
description: Eine andere Möglichkeit, eine Medienressource aufzulösen, ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medien-Stream erhalten möchten, ohne eine MediaPlayer-Instanz zu instanziieren.
title: Laden einer Medienressource mit MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Laden einer Medienressource mit MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

Eine andere Möglichkeit, eine Medienressource aufzulösen, ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medien-Stream erhalten möchten, ohne eine MediaPlayer-Instanz zu instanziieren.

Durch die `MediaPlayerItemLoader` -Klasse können Sie eine Medienressource für die entsprechende `MediaPlayerItem` , ohne eine Ansicht an eine `MediaPlayer` -Instanz, was zur Zuordnung der Hardware-Ressourcen für die Videodekodierung führen würde. Das Verfahren zum Abrufen der `MediaPlayerItem` -Instanz asynchron ist.

1. Implementieren von Ereignis-Listenern für diese `MediaPlayerItemLoader` events:

   * `MediaPlayerItemLoaderEvent.ERROR` event

     TVSDK verwendet dies, um Ihre Anwendung darüber zu informieren, dass ein Fehler aufgetreten ist. TVSDK stellt eine Fehlereigenschaft bereit, die Diagnoseinformationen enthält.

1. Registrieren Sie diese Instanz bei der `MediaPlayerItemLoader`.
1. Aufruf `DefaultMediaPlayerItemLoader.load`, wobei eine Instanz einer `MediaResource` -Objekt.

   Die URL der `MediaResource` -Objekt muss auf den Stream verweisen, für den Sie Informationen abrufen möchten. Beispiel:

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
