---
description: Eine andere Möglichkeit, eine Medienressource aufzulösen, ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medien-Stream erhalten möchten, ohne eine MediaPlayer-Instanz zu instanziieren.
title: Laden einer Medienressource mit MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Laden einer Medienressource mit MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Eine andere Möglichkeit, eine Medienressource aufzulösen, ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medien-Stream erhalten möchten, ohne eine MediaPlayer-Instanz zu instanziieren.

Durch die `MediaPlayerItemLoader` -Klasse können Sie eine Medienressource für die entsprechende `MediaPlayerItem` , ohne eine Ansicht an eine `MediaPlayer` -Instanz, was zur Zuordnung der Hardware-Ressourcen für die Videodekodierung führen würde. Das Verfahren zum Abrufen der `MediaPlayerItem` -Instanz asynchron ist.

1. Implementieren des `MediaPlayerItemLoader.LoaderListener` Callback-Oberfläche.

       Diese Schnittstelle definiert zwei Methoden:
   
   * `LoaderListener.onError` Callback-Funktion

     TVSDK verwendet dies, um Ihre Anwendung darüber zu informieren, dass ein Fehler aufgetreten ist. TVSDK stellt einen Fehlercode als Parameter und eine Beschreibungszeichenfolge bereit, die Diagnoseinformationen enthält.

   * `LoaderListener.onError` Callback-Funktion

     TVSDK verwendet dies, um Ihre Anwendung darüber zu informieren, dass die angeforderten Informationen in Form einer `MediaPlayerItem` -Instanz, die als Parameter an den Rückruf übergeben wird.

1. Registrieren Sie diese Instanz bei TVSDK, indem Sie sie als Parameter an den Konstruktor der `MediaPlayerItemLoader`.
1. Aufruf `MediaPlayerItemLoader.load`, wobei eine Instanz einer `MediaResource` -Objekt.

   Die URL der `MediaResource` -Objekt muss auf den Stream verweisen, für den Sie Informationen abrufen möchten. Beispiel:

   ```java
   // instantiate the listener interface 
   MediaPlayerItemLoader.LoaderListener _itemLoaderListener = 
     new MediaPlayerItemLoader.LoaderListener() { 
       @Override 
       public void onError(MediaErrorCode mediaErrorCode, String description) { 
           // something went wrong - look at the error code and description 
       } 
       @Override 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
           // information is available - look at the data in the "playerItem" object 
       } 
   } 
   
   // instantiate the MediaPlayerItemLoader object (pass the listener as parameter) 
   MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(_itemLoaderListener); 
   
   // create the MediaResource instance and set the URL to point to the actual media stream 
   MediaResource mediaResource =  
     MediaResource.createFromUrl("https://test.com/test_media.m3u8", null); 
   
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```
