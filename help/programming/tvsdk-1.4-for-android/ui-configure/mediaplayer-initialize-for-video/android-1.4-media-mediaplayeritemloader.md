---
description: Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.
seo-description: Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.
seo-title: Medienressource mit MediaPlayerItemLoader laden
title: Medienressource mit MediaPlayerItemLoader laden
uuid: b2311ddc-f059-4775-8553-fc354ec2636b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Medienressource mit MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader} laden

Eine andere Möglichkeit zum Auflösen einer Medienressource ist MediaPlayerItemLoader. Dies ist nützlich, wenn Sie Informationen zu einem bestimmten Medienstream abrufen möchten, ohne eine MediaPlayer-Instanz zu instanziieren.

Mithilfe der `MediaPlayerItemLoader`-Klasse können Sie eine Medienressource für die entsprechende `MediaPlayerItem`-Instanz austauschen, ohne eine Ansicht an eine `MediaPlayer`-Instanz anzuhängen, was zur Zuordnung der Videodekodierungs-Hardware-Ressourcen führen würde. Der Prozess zum Abrufen der `MediaPlayerItem`-Instanz ist asynchron.

1. Implementieren Sie die Callback-Schnittstelle `MediaPlayerItemLoader.LoaderListener`.

       Diese Schnittstelle definiert zwei Methoden:
   
   * `LoaderListener.onError` callback-Funktion

      TVSDK verwendet dies, um Ihre Anwendung darüber zu informieren, dass ein Fehler aufgetreten ist. TVSDK stellt einen Fehlercode als Parameter und eine Beschreibungszeichenfolge bereit, die diagnostische Informationen enthält.

   * `LoaderListener.onError` callback-Funktion

      TVSDK verwendet dies, um Ihre Anwendung darüber zu informieren, dass die angeforderten Informationen in Form einer `MediaPlayerItem`-Instanz verfügbar sind, die als Parameter an den Rückruf weitergeleitet wird.

1. Registrieren Sie diese Instanz bei TVSDK, indem Sie sie als Parameter an den Konstruktor von `MediaPlayerItemLoader` übergeben.
1. Rufen Sie `MediaPlayerItemLoader.load` auf und übergeben Sie eine Instanz eines `MediaResource`-Objekts.

   Die URL des Objekts `MediaResource` muss auf den Stream verweisen, für den Sie Informationen abrufen möchten. Beispiel:

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

