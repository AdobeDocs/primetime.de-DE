---
description: Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.
seo-description: Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.
seo-title: Wiedergabe anhalten und fortsetzen
title: Wiedergabe anhalten und fortsetzen
uuid: 229e2499-e30e-458c-bd6d-d035588c21cf
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---


# Wiedergabe anhalten und fortsetzen {#pause-and-resume-playback}

Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.

1. Überschreiben Sie `onPause` und `onResume` aus der Android-Aktivität.

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       requestAudioFocus(); 
       if (_lastKnownStatus == MediaPlayerStatus.PAUSED) { 
           _mediaPlayer.play(); 
       } 
   } 
   ... 
   
   @Override 
   public void onPause() { 
       super.onPause(); 
       if (_mediaPlayer != null) { 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING || 
             _mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) { 
               _savedPlayerStatus = _mediaPlayer.getStatus(); 
               _lastKnownTime = _mediaPlayer.getCurrentTime(); 
           } 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
               _mediaPlayer.pause(); 
               _lastKnownStatus = MediaPlayerStatus.PAUSED; 
           } 
       } 
   } 
   abandonAudioFocus(); 
   ```

