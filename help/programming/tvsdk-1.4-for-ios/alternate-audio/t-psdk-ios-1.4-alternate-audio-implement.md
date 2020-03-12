---
description: Spätbindende Audiodaten verwenden PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.
seo-description: Spätbindende Audiodaten verwenden PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.
seo-title: Zugriff auf alternative Audiospuren
title: Zugriff auf alternative Audiospuren
uuid: 77e39633-bf17-4a06-a2a1-93fdaadedd17
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Zugriff auf alternative Audiospuren{#access-alternate-audio-tracks}

Spätbindende Audiodaten verwenden PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.

1. Warten Sie, bis der MediaPlayer mindestens den `PTMediaPlayerStatusReady` Status erreicht hat.
1. Suchen Sie nach diesem Ereignis:

   Benachrichtigung `PTMediaPlayerItemMediaSelectionOptionsAvailable`: Die anfängliche Liste der Audiospuren ist verfügbar.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Rufen Sie die verfügbaren Audiospuren aus der `PTMediaPlayerItem` Instanz ab.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Legen Sie die ausgewählte Audiospur auf der `PTMediaPlayerItem` Instanz fest.
