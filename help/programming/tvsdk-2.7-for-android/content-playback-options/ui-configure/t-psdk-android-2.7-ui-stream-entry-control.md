---
description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
seo-description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
seo-title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
uuid: 65a19192-b890-4d69-9cb1-582a22988d2b
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein {#enter-a-stream-at-a-specific-time}

Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.

1. Übergeben Sie eine Position an `MediaPlayer.prepareToPlay`.

   TVSDK betrachtet die angegebene Position als Ausgangspunkt für das Asset und es ist kein Suchvorgang erforderlich. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, verwendet TVSDK die Standardposition. Weitere Informationen finden Sie unter [Laden einer Medienressource im Medienplayer](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md).

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

