---
description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 1%

---


# Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein.{#enter-a-stream-at-a-specific-time}

Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.

1. Übergeben Sie eine Position an `MediaPlayer.prepareToPlay`.

   TVSDK betrachtet die angegebene Position als Ausgangspunkt für das Asset und es ist kein Suchvorgang erforderlich. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, verwendet TVSDK die Standardposition. Weitere Informationen finden Sie unter [Medienressource im Medienplayer](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md) laden.

   Beispiel:

   ```java
   long desiredPostion = // TODO : choose a value; 
   @Override 
   public void onStatusChanged(MediaPlayerStatusChangedEvent statusChangedEvent) {   
       switch (statusChangedEvent.getStatus()) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
           case PREPARING: 
               showBufferingSpinner(); 
               break; 
       } 
   }
   ```

