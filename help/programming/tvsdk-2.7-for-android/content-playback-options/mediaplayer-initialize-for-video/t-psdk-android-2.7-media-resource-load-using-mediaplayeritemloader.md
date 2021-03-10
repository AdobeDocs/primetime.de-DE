---
description: Mit MediaPlayerItemLoader können Sie Informationen zu einem Medienstream abrufen, ohne eine MediaPlayer-Instanz zu instanziieren. Dies ist besonders nützlich, wenn Sie Streams vor dem Puffern zwischenspeichern möchten, damit die Wiedergabe ohne Verzögerung beginnen kann.
title: Medienressource mit MediaPlayerItemLoader laden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# Medienressource mit MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader} laden

Mit MediaPlayerItemLoader können Sie Informationen zu einem Medienstream abrufen, ohne eine MediaPlayer-Instanz zu instanziieren. Dies ist besonders nützlich, wenn Sie Streams vor dem Puffern zwischenspeichern möchten, damit die Wiedergabe ohne Verzögerung beginnen kann.

Mit der `MediaPlayerItemLoader`-Klasse können Sie eine Medienressource gegen die aktuelle `MediaPlayerItem`-Instanz austauschen, ohne eine Ansicht an eine `MediaPlayer`-Instanz anzuhängen, die Hardware-Ressourcen für die Videodekodierung zuweist. Weitere Schritte sind für DRM-geschützte Inhalte erforderlich, in diesem Handbuch werden sie jedoch nicht beschrieben.

>[!IMPORTANT]
>
>TVSDK unterstützt kein einzelnes `QoSProvider`, um sowohl mit `itemLoader` als auch mit `MediaPlayer` zu arbeiten. Wenn Ihre Anwendung Instant On verwendet, muss die Anwendung zwei `QoS`-Instanzen verwalten und beide Instanzen für die Informationen verwalten. Weitere Informationen finden Sie unter [SOFORT](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md).

1. Erstellen Sie eine Instanz von `MediaPlayerItemLoader`.

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
   
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
   
           public void onBufferingBegin() { 
               //Do something 
           } 
   
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       }); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   } 
   ```

   >[!TIP]
   >
   >Erstellen Sie für jede Ressource eine separate Instanz von `MediaPlayerItemLoader`. Verwenden Sie keine `MediaPlayerItemLoader`-Instanz, um mehrere Ressourcen zu laden.

1. Implementieren Sie die `ItemLoaderListener`-Klasse, um Benachrichtigungen von der `MediaPlayerItemLoader`-Instanz zu erhalten.

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
           public void onBufferingBegin() { 
               //Do something 
           } 
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       } ); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   }
   ```

   Führen Sie im Rückruf `onLoadComplete()` einen der folgenden Schritte aus:

   * Vergewissern Sie sich, dass alles, was sich auf die Pufferung auswirken könnte, z. B. die Auswahl von WebVTT oder Audiospuren, abgeschlossen ist, und rufen Sie `prepareBuffer()` auf, um die Vorteile des sofortigen Einsatzes zu nutzen.
   * Hängen Sie das Element mit `MediaPlayer` an die Instanz an, indem Sie `replaceCurrentItem()` verwenden.

   Wenn Sie `prepareBuffer()` aufrufen, erhalten Sie das Ereignis BUFFER_PREPARED im `onBufferPrepared`-Handler, wenn die Vorbereitung abgeschlossen ist.

1. Rufen Sie `load` auf der `MediaPlayerItemLoader`-Instanz auf und übergeben Sie die zu ladende Ressource sowie optional die Inhalts-ID und eine `MediaPlayerItemConfig`-Instanz.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Um einen Puffer von einem anderen Punkt als dem Anfang des Streams aus zu erstellen, rufen Sie `prepareBuffer()` mit der Position (in Millisekunden) auf, an der die Pufferung des Beginns erfolgen soll.
1. Verwenden Sie die `replaceCurrentItem()`- und `play()`-Methoden von `MediaPlayer`, um ab diesem Zeitpunkt die Wiedergabe des Beginns zu starten.
1. Warten Sie auf den Status &quot;Leerlauf&quot;und rufen Sie `replaceCurrentItem` auf.
1. Spielen Sie das Element ab.

   * Wenn das Element geladen, aber nicht gepuffert wird:

      1. Warten Sie auf den initialisierten Status.
      1. Aufruf von `prepareToPlay()`.
      1. Warten Sie auf den Status &quot;VORBEREITT&quot;.
      1. Aufruf von `play()`.
   * Wenn das Element gepuffert wird:

      1. Warten Sie auf das puffervorbereitete Ereignis.
      1. Aufruf von `play()`.