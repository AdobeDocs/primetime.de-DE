---
description: Standardmäßig beginnt beim Starten der Wiedergabe das VOD-Medium bei 0 (MediaPlayer.LIVE_POINT). Sie können das Standardverhalten überschreiben.
title: Stream zu einem bestimmten Zeitpunkt eingeben
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Stream zu einem bestimmten Zeitpunkt eingeben {#enter-a-stream-at-a-specific-time}

Standardmäßig beginnt beim Starten der Wiedergabe das VOD-Medium bei 0 (MediaPlayer.LIVE_POINT). Sie können das Standardverhalten überschreiben.

1. Übergeben einer Position an `MediaPlayer.prepareToPlay`.

   TVSDK betrachtet die angegebene Position als Ausgangspunkt für das Asset. Es ist kein Suchvorgang erforderlich. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, verwendet TVSDK die Standardposition.

   Beispiel:

   ```java
   long desiredPostion = //TODO : choose a value; 
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
               case PREPARING: 
               showBufferingSpinner(); 
               break; 
           ... 
       } 
   } 
   ```
