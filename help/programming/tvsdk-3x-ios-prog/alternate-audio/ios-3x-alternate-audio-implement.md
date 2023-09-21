---
description: Spätbindende Audio verwendet PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8 HLS-Wiedergabeliste spezifiziert ist und mehrere alternative Audio-Streams enthalten kann.
title: Auf alternative Audiospuren zugreifen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Auf alternative Audiospuren zugreifen {#access-alternate-audio-tracks}

Spätbindende Audio verwendet PTMediaPlayer, um ein Video abzuspielen, das in einer M3U8 HLS-Wiedergabeliste spezifiziert ist und mehrere alternative Audio-Streams enthalten kann.

1. Warten Sie, bis der MediaPlayer mindestens im `PTMediaPlayerStatusReady` -Status.
1. Suchen Sie nach diesem Ereignis:

   Benachrichtigung `PTMediaPlayerItemMediaSelectionOptionsAvailable`: Die erste Liste der Audiospuren ist verfügbar.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Rufen Sie die verfügbaren Audiospuren aus dem `PTMediaPlayerItem` -Instanz.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Festlegen des ausgewählten Audiotracks auf der `PTMediaPlayerItem` -Instanz.
