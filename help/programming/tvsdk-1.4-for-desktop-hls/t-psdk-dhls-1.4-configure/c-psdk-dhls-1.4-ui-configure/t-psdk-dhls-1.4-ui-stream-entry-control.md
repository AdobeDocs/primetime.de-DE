---
description: Standardmäßig beginnt beim Starten der Wiedergabe das VOD-Medium bei 0 und das Live-Medium am Client-Live-Point (DefaultMediaPlayer.LIVE_POINT).
title: Stream zu einem bestimmten Zeitpunkt eingeben
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Stream zu einem bestimmten Zeitpunkt eingeben{#enter-a-stream-at-a-specific-time}

Standardmäßig beginnt beim Starten der Wiedergabe das VOD-Medium bei 0 und das Live-Medium am Client-Live-Point (DefaultMediaPlayer.LIVE_POINT).

Übergeben einer Position an `MediaPlayer.prepareToPlay`.

TVSDK betrachtet die angegebene Position als Ausgangspunkt für das Asset. Es ist kein Suchvorgang erforderlich. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, verwendet die Standardposition.

Beispiel:

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
