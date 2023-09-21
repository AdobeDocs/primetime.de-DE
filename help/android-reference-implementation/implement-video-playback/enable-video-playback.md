---
description: Erstellen Sie einen Play-backManager, der die HLS-Stream-Einrichtung und -Wiedergabe verarbeitet. Es ist keine andere Konfiguration erforderlich.
title: Videowiedergabe aktivieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Videowiedergabe aktivieren {#enable-video-playback}

Erstellen Sie einen Play-backManager, der die HLS-Stream-Einrichtung und -Wiedergabe verarbeitet. Es ist keine andere Konfiguration erforderlich.

1. Erstellen Sie das Medienplayer-Objekt, indem Sie sicherstellen, dass der folgende Code in [!DNL PlayerFragment.java]:

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. Erstellen Sie den Wiedergabe-Manager über das `ManagerFactory`:

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. Implementieren des `PlaybackManagerEventListener` im `PlayerFragment` um die Wiedergabeereignisse zu verarbeiten:

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. Registrieren Sie den Ereignis-Listener im `PlayerFragment`:

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. Richten Sie die Videoressource ein:

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. Richten Sie die Vorgänge der Steuerleiste im `PlayerFragment`:

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## Verwandte API-Dokumentation {#related-api-documentation}

* [Klasse PlaybackManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)
