---
description: Standardmäßig beginnt beim Starten der Wiedergabe das VOD-Medium bei 0 und das Live-Medium am Client-Live-Point (MediaPlayer.LIVE_POINT). Sie können das Standardverhalten überschreiben.
title: Stream zu einem bestimmten Zeitpunkt eingeben
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Stream zu einem bestimmten Zeitpunkt eingeben {#enter-a-stream-at-a-specific-time}

Standardmäßig beginnt beim Starten der Wiedergabe das VOD-Medium bei 0 und das Live-Medium am Client-Live-Point (MediaPlayer.LIVE_POINT). Sie können das Standardverhalten überschreiben.

1. Übergeben einer Position an `MediaPlayer.prepareToPlay`.

   TVSDK betrachtet die angegebene Position als Ausgangspunkt für das Asset und es ist kein Suchvorgang erforderlich. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, verwendet TVSDK die Standardposition. Weitere Informationen finden Sie unter [Laden einer Medienressource im Medienplayer](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md).

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
