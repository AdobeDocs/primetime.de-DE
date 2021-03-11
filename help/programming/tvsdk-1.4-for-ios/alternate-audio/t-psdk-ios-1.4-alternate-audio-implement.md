---
description: Spätbindende Audiodaten verwenden PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.
title: Zugriff auf alternative Audiospuren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Zugriff auf alternative Audiospuren{#access-alternate-audio-tracks}

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
