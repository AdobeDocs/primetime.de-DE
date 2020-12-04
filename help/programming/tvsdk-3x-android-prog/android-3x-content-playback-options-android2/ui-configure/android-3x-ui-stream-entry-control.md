---
description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
seo-description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.
seo-title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
uuid: b315a967-77ad-4352-8a32-f228704d4b20
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 1%

---


# Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein.{#enter-a-stream-at-a-specific-time}

Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gestartet. Sie können das Standardverhalten überschreiben.

1. Übergeben Sie eine Position an `MediaPlayer.prepareToPlay`.

   TVSDK betrachtet die angegebene Position als Ausgangspunkt für das Asset und es ist kein Suchvorgang erforderlich. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, verwendet TVSDK die Standardposition. Weitere Informationen finden Sie unter [Medienressource im Medienplayer](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md) laden.

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
