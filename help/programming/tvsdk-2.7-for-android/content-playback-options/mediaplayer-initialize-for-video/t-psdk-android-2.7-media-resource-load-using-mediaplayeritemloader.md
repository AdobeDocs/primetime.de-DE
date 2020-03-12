---
description: Mit MediaPlayerItemLoader können Sie Informationen zu einem Medienstream abrufen, ohne eine MediaPlayer-Instanz zu instanziieren. Dies ist besonders nützlich, wenn Sie Streams vor dem Puffern zwischenspeichern möchten, damit die Wiedergabe ohne Verzögerung beginnen kann.
seo-description: Mit MediaPlayerItemLoader können Sie Informationen zu einem Medienstream abrufen, ohne eine MediaPlayer-Instanz zu instanziieren. Dies ist besonders nützlich, wenn Sie Streams vor dem Puffern zwischenspeichern möchten, damit die Wiedergabe ohne Verzögerung beginnen kann.
seo-title: Medienressource mit MediaPlayerItemLoader laden
title: Medienressource mit MediaPlayerItemLoader laden
uuid: 43ca2470-1fd2-4f66-94fe-a12ed17b52d7
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Medienressource mit MediaPlayerItemLoader laden {#load-a-media-resource-using-mediaplayeritemloader}

Mit MediaPlayerItemLoader können Sie Informationen zu einem Medienstream abrufen, ohne eine MediaPlayer-Instanz zu instanziieren. Dies ist besonders nützlich, wenn Sie Streams vor dem Puffern zwischenspeichern möchten, damit die Wiedergabe ohne Verzögerung beginnen kann.

Mit der `MediaPlayerItemLoader` Klasse können Sie eine Medienressource gegen die aktuelle Version austauschen, `MediaPlayerItem` ohne eine Ansicht an eine `MediaPlayer` Instanz anzuhängen, die die Hardware-Ressourcen für die Videodekodierung zuordnet. Weitere Schritte sind für DRM-geschützte Inhalte erforderlich, in diesem Handbuch werden sie jedoch nicht beschrieben.

>[!IMPORTANT]
>
>TVSDK unterstützt keine einzelne `QoSProvider` für die Verwendung sowohl `itemLoader` als auch `MediaPlayer`. Wenn Ihre Anwendung Instant On verwendet, muss die Anwendung zwei `QoS` Instanzen verwalten und beide Instanzen für die Informationen verwalten. Weitere Informationen finden Sie unter [Sofort-On](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md) .

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
   >Erstellen Sie eine separate Instanz von `MediaPlayerItemLoader` für jede Ressource. Verwenden Sie nicht eine `MediaPlayerItemLoader` Instanz, um mehrere Ressourcen zu laden.

1. Implementieren Sie die `ItemLoaderListener` Klasse, um Benachrichtigungen von der `MediaPlayerItemLoader` Instanz zu erhalten.

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

   Führen Sie im `onLoadComplete()` Rückruf einen der folgenden Schritte aus:

   * Vergewissern Sie sich, dass alles, was sich auf die Pufferung auswirken könnte, z. B. die Auswahl von WebVTT- oder Audiospuren, abgeschlossen ist, und rufen Sie an, `prepareBuffer()` um die Vorteile von &quot;Sofort on On&quot;zu nutzen.
   * Hängen Sie das Element mithilfe von `MediaPlayer` an die `replaceCurrentItem()`Instanz an.
   Wenn Sie anrufen `prepareBuffer()`, erhalten Sie das Ereignis BUFFER_PREPARED im `onBufferPrepared` Handler, wenn die Vorbereitung abgeschlossen ist.

1. Rufen Sie `load` die `MediaPlayerItemLoader` Instanz auf und übergeben Sie die zu ladende Ressource, optional die Inhalts-ID und eine `MediaPlayerItemConfig` Instanz.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Um einen Puffer von einem anderen Zeitpunkt als dem Anfang des Streams aus zu erstellen, rufen Sie `prepareBuffer()` mit der Position (in Millisekunden) auf, an der die Pufferung des Beginns erfolgen soll.
1. Verwenden Sie die `replaceCurrentItem()` und- `play()` `MediaPlayer` Methoden, um ab diesem Zeitpunkt die Wiedergabe des Beginns zu starten.
1. Warten Sie auf den Status &quot;Leerlauf&quot;und rufen Sie `replaceCurrentItem`an.
1. Spielen Sie das Element ab.

   * Wenn das Element geladen, aber nicht gepuffert wird:

      1. Warten Sie auf den initialisierten Status.
      1. Ruf `prepareToPlay()`.
      1. Warten Sie auf den Status &quot;VORBEREITT&quot;.
      1. Ruf `play()`.
   * Wenn das Element gepuffert wird:

      1. Warten Sie auf das puffervorbereitete Ereignis.
      1. Ruf `play()`.