---
description: Sie können eine Spur aus einer Liste von derzeit verfügbaren Untertitelspuren auswählen. Dies wird zur aktuellen Spur, die angezeigt wird, wenn die Sichtbarkeit aktiviert ist. Einige Tracks sind möglicherweise nicht verfügbar, also suchen Sie nach dem Ereignis, das anzeigt, dass mehr verfügbar sind.
seo-description: Sie können eine Spur aus einer Liste von derzeit verfügbaren Untertitelspuren auswählen. Dies wird zur aktuellen Spur, die angezeigt wird, wenn die Sichtbarkeit aktiviert ist. Einige Tracks sind möglicherweise nicht verfügbar, also suchen Sie nach dem Ereignis, das anzeigt, dass mehr verfügbar sind.
seo-title: Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren
title: Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren
uuid: d582779a-2789-4e2a-85f6-1a0b9b847382
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---


# Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren {#select-a-current-caption-track-from-among-available-tracks}

Sie können eine Spur aus einer Liste von derzeit verfügbaren Untertitelspuren auswählen. Dies wird zur aktuellen Spur, die angezeigt wird, wenn die Sichtbarkeit aktiviert ist. Einige Tracks sind möglicherweise nicht verfügbar, also suchen Sie nach dem Ereignis, das anzeigt, dass mehr verfügbar sind.

1. Warten Sie, bis sich der Medienplayer mindestens im Status `PREPARED` befindet.
1. Suchen Sie nach diesen Ereignissen:

   * `MediaPlayerEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.INITIALIZED`: Die anfängliche Liste von Untertitelspuren ist verfügbar.

1. Hier erhalten Sie eine Liste aller derzeit verfügbaren Untertitel-Tracks.

   Beispiel:

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
     mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. Wählen Sie eine verfügbare Spur als aktuelle Spur aus.

   Beispiel:

   ```java
   // Select the initial CC track. 
   for (int i = 0; i < ccTracks.size(); i++) { 
       ClosedCaptionsTrack track = ccTracks.get(i); 
       if (track.getName().equals(INITIAL_CC_TRACK)) { 
       <b>mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track);</b> 
             selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. Implementieren Sie einen Listener für das Ereignis, der angibt, dass mehr Tracks verfügbar sind. Wenn TVSDK das Ereignis auslöst, rufen Sie die aktuelle Liste der verfügbaren Tracks ab.

   Rufen Sie die Liste jedes Mal ab, wenn das Ereignis eintritt, um sicherzustellen, dass Sie immer über die aktuellste Liste verfügen.