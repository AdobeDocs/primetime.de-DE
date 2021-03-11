---
description: Erstellen Sie einen PlaybackManager, der den HLS-Stream-Setup und -Wiedergabe-Vorgang verarbeitet. Es ist keine andere Konfiguration erforderlich.
title: Aktivieren der Videowiedergabe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Aktivieren der Videowiedergabe {#enable-video-playback}

Erstellen Sie einen PlaybackManager, der den HLS-Stream-Setup und -Wiedergabe-Vorgang verarbeitet. Es ist keine andere Konfiguration erforderlich.

1. Erstellen Sie das Medienplayer-Objekt, indem Sie sicherstellen, dass der folgende Code in [!DNL PlayerFragment.java] vorhanden ist:

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

1. Implementieren Sie `PlaybackManagerEventListener` in `PlayerFragment`, um die Wiedergabe-Ereignis zu verarbeiten:

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. Registrieren Sie den Ereignis-Listener in `PlayerFragment`:

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. Einrichten der Videoressource:

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. Richten Sie die Vorgänge der Steuerleiste in `PlayerFragment` ein:

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