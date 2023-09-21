---
description: Sie können einen Track aus einer Liste mit derzeit verfügbaren Untertitelspuren auswählen. Dies wird zum aktuellen Track, der angezeigt wird, wenn die Sichtbarkeit aktiviert ist. Einige Tracks sind anfangs möglicherweise nicht verfügbar. Achten Sie daher auf das Ereignis, das angibt, dass mehr verfügbar sind.
title: Wählen Sie einen aktuellen Untertitelpfad aus den verfügbaren Tracks aus.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Wählen Sie einen aktuellen Untertitelpfad aus den verfügbaren Tracks aus. {#select-a-current-caption-track-from-among-available-tracks}

Sie können einen Track aus einer Liste mit derzeit verfügbaren Untertitelspuren auswählen. Dies wird zum aktuellen Track, der angezeigt wird, wenn die Sichtbarkeit aktiviert ist. Einige Tracks sind anfangs möglicherweise nicht verfügbar. Achten Sie daher auf das Ereignis, das angibt, dass mehr verfügbar sind.

1. Warten Sie, bis der Medienplayer mindestens im `PREPARED` -Status.
1. Suchen Sie nach diesen Ereignissen:

   * `MediaPlayerEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.INITIALIZED`: Die anfängliche Liste der Tracks mit geschlossenen Untertiteln ist verfügbar.

1. Rufen Sie eine Liste aller derzeit verfügbaren Tracks mit geschlossenen Untertiteln ab.

   Beispiel:

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
     mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. Wählen Sie eine verfügbare Spur aus, um die aktuelle Spur zu sein.

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

1. Implementieren Sie einen Listener für das Ereignis, der anzeigt, dass mehr Tracks verfügbar sind. Wenn TVSDK das Ereignis sendet, rufen Sie die aktuelle Liste der verfügbaren Tracks ab.

   Rufen Sie die Liste jedes Mal ab, wenn das Ereignis eintritt, um sicherzustellen, dass Sie immer über die aktuellste Liste verfügen.
