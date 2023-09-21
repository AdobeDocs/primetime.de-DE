---
description: Wenn die Wiedergabe gestartet wird, beginnt das VOD-Medium standardmäßig bei 0 und das Live-Medium beginnt am Client-Live-Point (MediaPlayer.LIVE_POINT). Sie können das Standardverhalten überschreiben.
title: Stream zu einem bestimmten Zeitpunkt eingeben
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Stream zu einem bestimmten Zeitpunkt eingeben{#enter-a-stream-at-a-specific-time}

Wenn die Wiedergabe gestartet wird, beginnt das VOD-Medium standardmäßig bei 0 und das Live-Medium beginnt am Client-Live-Point (MediaPlayer.LIVE_POINT). Sie können das Standardverhalten überschreiben.

1. Übergeben einer Position an `MediaPlayer.prepareToPlay`.
1. Browser TVSDK verwendet diese Position als Ausgangspunkt für das Asset.

   >[!NOTE]
   >
   >Es ist kein Suchvorgang erforderlich.

1. Wenn sich die Position nicht innerhalb des suchbaren Bereichs befindet, werden die Standardpositionen verwendet.

   Beispiel:

   ```js
   var desiredPostion = //choose a value; 
   onStatusChange = function (event) { 
       case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
           console.log("Player Status: INITIALIZED"); 
           player.prepareToPlay(desiredPostion); 
           break; 
   } 
   ```
