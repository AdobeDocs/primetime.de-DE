---
description: Spätbindende Audio verwendet MediaPlayer zum Abspielen eines Videos, das in einer M3U8 HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.
title: Auf alternative Audiospuren zugreifen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Auf alternative Audiospuren zugreifen{#access-alternate-audio-tracks}

Spätbindende Audio verwendet MediaPlayer zum Abspielen eines Videos, das in einer M3U8 HLS-Wiedergabeliste angegeben ist und mehrere alternative Audio-Streams enthalten kann.

1. Warten Sie auf die `MediaPlayer` mindestens den Status VORBEREITET haben.
1. Suchen Sie nach diesen Ereignissen:

   * `MediaPlayerItemEvent.ITEM_CREATED`: Die erste Liste der Audiospuren ist verfügbar.
   * `MediaPlayerItemEvent.AUDIO_UPDATED`: Audiospuren wurden während der Wiedergabe geändert

1. Rufen Sie die verfügbaren Audiospuren aus dem `MediaPlayerItem` -Instanz.
1. (Optional) Präsentieren Sie dem Benutzer die verfügbaren Tracks.
1. Festlegen des ausgewählten Audiotracks auf der `MediaPlayerItem` -Instanz.
