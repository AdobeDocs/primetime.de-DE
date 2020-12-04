---
description: Spätbindende Audiodaten verwenden MediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.
seo-description: Spätbindende Audiodaten verwenden MediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.
seo-title: Zugriff auf alternative Audiospuren
title: Zugriff auf alternative Audiospuren
uuid: c7060022-29ec-43c1-811b-41cca5f5356c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Zugriff auf alternative Audiospuren{#access-alternate-audio-tracks}

Spätbindende Audiodaten verwenden MediaPlayer, um ein Video abzuspielen, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.

1. Warten Sie, bis der MediaPlayer mindestens den Status &quot;VORBEREITT&quot;aufweist.
1. Suchen Sie nach diesem Ereignis:

   `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: Die anfängliche Liste der Audiospuren ist verfügbar.

1. Rufen Sie die verfügbaren Audiospuren von der `MediaPlayerItem`-Instanz ab.

   `mediaPlayerItem.getAudioTracks()` 1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Legen Sie die ausgewählte Audiospur auf der `MediaPlayerItem`-Instanz fest.

   `mediaPlayerItem.selectAudioTrack(audioTrack)`