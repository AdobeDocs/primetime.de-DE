---
description: Standardmäßig werden bei Wiedergabe-Beginn VOD-Media-Beginn bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gesendet. Sie können das Standardverhalten überschreiben.
seo-description: Standardmäßig werden bei Wiedergabe-Beginn VOD-Media-Beginn bei 0 und Live-Media-Beginn am Live-Point des Clients (MediaPlayer.LIVE_POINT) gesendet. Sie können das Standardverhalten überschreiben.
seo-title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
title: Geben Sie einen Stream zu einem bestimmten Zeitpunkt ein
uuid: 5db73b50-0629-4fb1-8f12-6c88e4cd7109
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '136'
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

