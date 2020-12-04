---
description: Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.
seo-description: Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.
seo-title: Medienressource mit MediaPlayerItemLoader laden
title: Medienressource mit MediaPlayerItemLoader laden
uuid: a7ec8f58-7357-4757-a402-e879dd6caec8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Medienressource mit MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader} laden

Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.

Mithilfe der `MediaPlayerItemLoader`-Klasse können Sie eine Medienressource für die entsprechende `MediaPlayerItem`-Instanz austauschen, ohne eine Ansicht an eine `MediaPlayer`-Instanz anzuhängen, was zur Zuordnung der Videodekodierungs-Hardware-Ressourcen führen würde. Der Prozess zum Abrufen der `MediaPlayerItem`-Instanz ist asynchron.

1. Implementieren Sie Ereignis-Listener für diese `MediaPlayerItemLoader`-Ereignis:

   * `MediaPlayerItemLoaderEvent.ERROR` ereignis

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

