---
description: Standardmäßig werden bei Wiedergabe-Beginn VOD-Media-Beginn bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gesendet. Sie können das Standardverhalten überschreiben.
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 1%

---


# Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein{#enter-a-stream-at-a-specific-time}

Standardmäßig werden bei Wiedergabe-Beginn VOD-Media-Beginn bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gesendet. Sie können das Standardverhalten überschreiben.

1. Übergeben Sie eine Position an `MediaPlayer.prepareToPlay`.
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

