---
description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

---


# Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein.{#enter-a-stream-at-a-specific-time}

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

