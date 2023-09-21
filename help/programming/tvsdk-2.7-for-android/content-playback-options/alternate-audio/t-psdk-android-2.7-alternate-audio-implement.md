---
description: Alternatives Audio verwendet MediaPlayer zum Abspielen eines Videos, das in einer M3U8 HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.
title: Auf alternative Audiospuren zugreifen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Auf alternative Audiospuren zugreifen {#access-alternate-audio-tracks}

Alternatives Audio verwendet MediaPlayer zum Abspielen eines Videos, das in einer M3U8 HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.

1. Warten Sie auf die `MediaPlayer` mindestens in `MediaPlayerStatus.PREPARED` -Status.
1. Suchen Sie nach `MediaPlayerEvent.STATUS_CHANGED` Ereignis mit Status `MediaPlayerStatus.PREPARED`.

   Dieser Schritt bedeutet, dass die ursprüngliche Liste der Audiospuren verfügbar ist.

1. Rufen Sie die verfügbaren Audiospuren aus dem `MediaPlayerItem` -Instanz.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Festlegen des ausgewählten Audiotracks auf der `MediaPlayerItem` -Instanz.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```
