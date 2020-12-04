---
description: Alternativaudio verwendet MediaPlayer zur Wiedergabe eines Videos, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.
seo-description: Alternativaudio verwendet MediaPlayer zur Wiedergabe eines Videos, das in einer M3U8-HLS-Wiedergabeliste angegeben ist und mehrere alternative Audiostreams enthalten kann.
seo-title: Zugriff auf alternative Audiospuren
title: Zugriff auf alternative Audiospuren
uuid: 09aa00e9-0cbf-4f5b-9652-ce514f6e2f38
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---


# Zugriff auf alternative Audiospuren{#access-alternate-audio-tracks}

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
