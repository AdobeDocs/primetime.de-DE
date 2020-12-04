---
description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (DefaultMediaPlayer.LIVE_POINT) gestartet.
seo-description: Standardmäßig werden VOD-Medien-Beginn beim Starten der Wiedergabe bei 0 und Live-Media-Beginn am Live-Point des Clients (DefaultMediaPlayer.LIVE_POINT) gestartet.
seo-title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
uuid: f58d908a-77b9-465f-b3a9-8fe63a249d39
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 1%

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
