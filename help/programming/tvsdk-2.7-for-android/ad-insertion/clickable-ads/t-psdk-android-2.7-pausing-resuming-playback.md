---
description: Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.
title: Wiedergabe anhalten und fortsetzen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '46'
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

