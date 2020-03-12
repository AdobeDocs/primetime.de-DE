---
description: Spätbindende Audiodaten verwenden MediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.
seo-description: Spätbindende Audiodaten verwenden MediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.
seo-title: Zugriff auf alternative Audiospuren
title: Zugriff auf alternative Audiospuren
uuid: 136b4f1b-e56f-4a8a-a961-05193434558c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Zugriff auf alternative Audiospuren{#access-alternate-audio-tracks}

Spätbindende Audiodaten verwenden MediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.

1. Warten Sie, bis der Status &quot;VORBEREITET&quot; `MediaPlayer` mindestens vorliegt.
1. Suchen Sie nach diesen Ereignissen:

   * `MediaPlayerItemEvent.ITEM_CREATED`: Die anfängliche Liste der Audiospuren ist verfügbar.
   * `MediaPlayerItemEvent.AUDIO_UPDATED`: Während der Wiedergabe wurden Audiospuren geändert

1. Rufen Sie die verfügbaren Audiospuren aus der `MediaPlayerItem` Instanz ab.
1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Legen Sie die ausgewählte Audiospur auf der `MediaPlayerItem` Instanz fest.
