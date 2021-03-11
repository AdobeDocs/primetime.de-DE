---
description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
title: Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 1%

---


# Wählen Sie eine aktuelle Untertitelspur unter den verfügbaren Spuren aus.{#select-a-current-caption-track-from-among-available-tracks}

Sie können eine Spur aus einer Liste von derzeit verfügbaren Untertitelspuren auswählen. Dies wird zur aktuellen Spur, die angezeigt wird, wenn die Sichtbarkeit aktiviert ist. Einige Tracks sind möglicherweise nicht verfügbar, also suchen Sie nach dem Ereignis, das anzeigt, dass mehr verfügbar sind.

>[!TIP]
>
>Untertitel sind immer aktiviert. Alle standardmäßigen Untertitelspuren gelten als vorhanden. Standardspuren (z. B. CC1-CC4, CS1-CS6) werden in `ClosedCaptionsTrack.DefaultCCTypes` aufgezählt. Wenn die Wiedergabe beginnt, sucht TVSDK auf einem dieser Kanal nach Aktivität. Wenn Aktivität gefunden wird, legt sie die `isActive`-Methode für diese Verfolgung fest und löst das `MediaPlayer.PlaybackEventListener.onUpdated`-Ereignis aus.

1. Warten Sie, bis der Medienplayer mindestens den Status &quot;VORBEREITT&quot;aufweist.
1. Suchen Sie nach diesen Ereignissen:

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: Die anfängliche Liste von Tracks mit Untertiteln ist verfügbar

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
           mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track); 
           selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. Implementieren Sie einen Listener für das Ereignis, der angibt, dass mehr Tracks verfügbar sind. Wenn TVSDK das Ereignis auslöst, rufen Sie die aktuelle Liste der verfügbaren Tracks ab.

   Rufen Sie die Liste jedes Mal ab, wenn das Ereignis eintritt, um sicherzustellen, dass Sie immer über die aktuellste Liste verfügen.
