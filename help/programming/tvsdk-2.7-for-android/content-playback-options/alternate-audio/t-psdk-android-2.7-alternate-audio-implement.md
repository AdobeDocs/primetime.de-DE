---
description: Alternativaudio verwendet MediaPlayer zur Wiedergabe eines Videos, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.
title: Zugriff auf alternative Audiospuren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Zugriff auf alternative Audiospuren {#access-alternate-audio-tracks}

Alternativaudio verwendet MediaPlayer zur Wiedergabe eines Videos, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.

1. Warten Sie, bis `MediaPlayer` sich mindestens im Status `MediaPlayerStatus.PREPARED` befindet.
1. Suchen Sie nach dem Ereignis `MediaPlayerEvent.STATUS_CHANGED` mit dem Status `MediaPlayerStatus.PREPARED`.

   Dieser Schritt bedeutet, dass die anfängliche Liste der Audiospuren verfügbar ist.

1. Rufen Sie die verfügbaren Audiospuren von der `MediaPlayerItem`-Instanz ab.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Legen Sie die ausgewählte Audiospur auf der `MediaPlayerItem`-Instanz fest.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```

