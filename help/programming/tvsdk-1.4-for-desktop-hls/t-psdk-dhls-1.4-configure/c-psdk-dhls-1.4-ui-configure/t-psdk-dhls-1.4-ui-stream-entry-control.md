---
description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (DefaultMediaPlayer.LIVE_POINT) gestartet.
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

---


# Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein{#enter-a-stream-at-a-specific-time}

Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (DefaultMediaPlayer.LIVE_POINT) gestartet.

Übergeben Sie eine Position an `MediaPlayer.prepareToPlay`.

TVSDK betrachtet die angegebene Position als Ausgangspunkt für das Asset. Es ist kein Suchvorgang erforderlich. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, wird die Standardposition verwendet.

Beispiel:

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
