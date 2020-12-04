---
description: Spätbindende Audiodaten verwenden PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.
seo-description: Spätbindende Audiodaten verwenden PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.
seo-title: Zugriff auf alternative Audiospuren
title: Zugriff auf alternative Audiospuren
uuid: 2915a74f-5ec3-457e-890d-5c79be39f37a
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Zugriff auf alternative Audiospuren {#access-alternate-audio-tracks}

Spätbindende Audiodaten verwenden PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.

1. Warten Sie, bis der MediaPlayer mindestens den Status `PTMediaPlayerStatusReady` hat.
1. Suchen Sie nach diesem Ereignis:

   notification `PTMediaPlayerItemMediaSelectionOptionsAvailable`: Die anfängliche Liste der Audiospuren ist verfügbar.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Rufen Sie die verfügbaren Audiospuren von der `PTMediaPlayerItem`-Instanz ab.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Legen Sie die ausgewählte Audiospur auf der `PTMediaPlayerItem`-Instanz fest.
