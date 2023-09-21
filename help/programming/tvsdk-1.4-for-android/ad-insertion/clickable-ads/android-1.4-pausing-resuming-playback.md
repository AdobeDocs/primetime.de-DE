---
description: Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.
title: Wiedergabe anhalten und fortsetzen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Wiedergabe anhalten und fortsetzen {#pause-and-resume-playback}

Wenn ein Benutzer auf eine Anzeige klickt, sollte Ihre Anwendung die Wiedergabe des Hauptvideoinhalts anhalten.

Überschreiben Sie die `onPause` und `onResume` über die Android-Aktivität aus.

```java
@Override 
public void onResume() { 
    super.onResume(); 
    requestAudioFocus(); 
    if (_lastKnownStatus == MediaPlayer.PlayerState.PAUSED) { 
        _mediaPlayer.play(); 
    } 
} 
... 
 
@Override 
public void onPause() { 
    super.onPause(); 
    if (_mediaPlayer != null) { 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING || 
          _mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) { 
            _savedPlayerState = _mediaPlayer.getStatus(); 
            _lastKnownTime = _mediaPlayer.getCurrentTime(); 
        } 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING) { 
            _mediaPlayer.pause(); 
            _lastKnownStatus = MediaPlayer.PlayerState.PAUSED; 
        } 
    } 
} 
 
abandonAudioFocus(); 
```
