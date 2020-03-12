---
description: Erstellen Sie einen PlaybackManager, der den HLS-Stream-Setup und -Wiedergabe-Vorgang verarbeitet. Es ist keine andere Konfiguration erforderlich.
seo-description: Erstellen Sie einen PlaybackManager, der den HLS-Stream-Setup und -Wiedergabe-Vorgang verarbeitet. Es ist keine andere Konfiguration erforderlich.
seo-title: Aktivieren der Videowiedergabe
title: Aktivieren der Videowiedergabe
uuid: ddc0defa-c40f-4ee6-a69f-d5eeca6c2fce
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# Aktivieren der Videowiedergabe {#enable-video-playback}

Erstellen Sie einen PlaybackManager, der den HLS-Stream-Setup und -Wiedergabe-Vorgang verarbeitet. Es ist keine andere Konfiguration erforderlich.

1. Erstellen Sie das Medienplayer-Objekt, indem Sie sicherstellen, dass der folgende Code in vorhanden ist [!DNL PlayerFragment.java]:

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. Erstellen Sie den Wiedergabe-Manager über `ManagerFactory`:

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. Implementieren Sie die `PlaybackManagerEventListener` in, um die Wiedergabe-Ereignis zu verarbeiten `PlayerFragment` :

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. Registrieren Sie den Ereignis-Listener im `PlayerFragment`:

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. Einrichten der Videoressource:

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. Richten Sie die Steuerleistenvorgänge in der `PlayerFragment`:

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