---
description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
seo-description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
seo-title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
uuid: ac3479e2-46a1-4ac8-a9e8-68a23f5dd74d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein {#enter-a-stream-at-a-specific-time}

Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.

1. Übergeben Sie eine Position an `MediaPlayer.prepareToPlay`.

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

