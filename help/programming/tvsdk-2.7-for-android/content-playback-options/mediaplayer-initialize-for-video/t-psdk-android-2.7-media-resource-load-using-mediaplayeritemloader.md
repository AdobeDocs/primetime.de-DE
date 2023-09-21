---
description: Mit MediaPlayerItemLoader können Sie Informationen zu einem Medien-Stream abrufen, ohne eine MediaPlayer-Instanz zu instanziieren. Dies ist besonders bei der Vorab-Pufferung von Streams nützlich, damit die Wiedergabe ohne Verzögerung beginnen kann.
title: Laden einer Medienressource mit MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Laden einer Medienressource mit MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Mit MediaPlayerItemLoader können Sie Informationen zu einem Medien-Stream abrufen, ohne eine MediaPlayer-Instanz zu instanziieren. Dies ist besonders bei der Vorab-Pufferung von Streams nützlich, damit die Wiedergabe ohne Verzögerung beginnen kann.

Die `MediaPlayerItemLoader` -Klasse hilft Ihnen beim Austausch einer Medienressource für die aktuelle `MediaPlayerItem` , ohne eine Ansicht an eine `MediaPlayer` -Instanz, die Hardware-Ressourcen für die Videodekodierung zuweist. Für DRM-geschützte Inhalte sind zusätzliche Schritte erforderlich, diese werden jedoch in diesem Handbuch nicht beschrieben.

>[!IMPORTANT]
>
>TVSDK unterstützt keine einzelne `QoSProvider` für beide `itemLoader` und `MediaPlayer`. Wenn Ihre Anwendung Instant On verwendet, muss die Anwendung zwei `QoS` Instanzen und verwalten Sie beide Instanzen für die Informationen. Siehe  [Sofortzugriff](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md) für weitere Informationen.

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
   >Erstellen Sie eine separate Instanz von `MediaPlayerItemLoader` für jede Ressource. Verwenden Sie keinen `MediaPlayerItemLoader` -Instanz, um mehrere Ressourcen zu laden.

1. Implementieren des `ItemLoaderListener` -Klasse zum Empfangen von Benachrichtigungen von `MediaPlayerItemLoader` -Instanz.

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

   Im `onLoadComplete()` Callback ausführen, führen Sie einen der folgenden Schritte aus:

   * Stellen Sie sicher, dass alles, was sich auf die Pufferung auswirken könnte, z. B. Auswählen von WebVTT- oder Audio-Tracks, abgeschlossen ist und aufruft `prepareBuffer()` , um die Vorteile von sofortiger Verwendung zu nutzen.
   * Hängen Sie das Element an die `MediaPlayer` -Instanz mithilfe von `replaceCurrentItem()`.

   Wenn Sie `prepareBuffer()`, erhalten Sie das Ereignis &quot;BUFFER_PREPARED&quot;in Ihrem `onBufferPrepared` Handler, wenn die Vorbereitung abgeschlossen ist.

1. Aufruf `load` auf `MediaPlayerItemLoader` -Instanz und übergeben Sie die zu ladende Ressource sowie optional die Inhalts-ID und eine `MediaPlayerItemConfig` -Instanz.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Rufen Sie auf, um von einem anderen Punkt als dem Anfang des Streams aus zu puffern. `prepareBuffer()` mit der Position (in Millisekunden), an der die Pufferung gestartet werden soll.
1. Verwenden Sie die `replaceCurrentItem()` und `play()` Methoden `MediaPlayer` um ab diesem Zeitpunkt mit dem Abspielen zu beginnen.
1. Warten auf Leerlaufstatus und Aufruf `replaceCurrentItem`.
1. Spiel das Element ab.

   * Wenn das Element geladen, aber nicht gepuffert wird:

      1. Warten Sie auf den initialisierten Status.
      1. Aufruf `prepareToPlay()`.
      1. Warten Sie auf den Status VORBEREITT .
      1. Aufruf `play()`.

   * Wenn das Element gepuffert wird:

      1. Warten Sie auf das Ereignis, das vom Puffer vorbereitet wurde.
      1. Aufruf `play()`.
