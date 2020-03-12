---
description: Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.
seo-description: Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.
seo-title: Wiedergabe anhalten und fortsetzen
title: Wiedergabe anhalten und fortsetzen
uuid: 87ba9f05-912d-4b85-8add-feb26a796a3a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Wiedergabe anhalten und fortsetzen {#pause-and-resume-playback}

Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.

1. Überschreiben Sie die `onPause` und `onResume` die Android-Aktivität.

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

