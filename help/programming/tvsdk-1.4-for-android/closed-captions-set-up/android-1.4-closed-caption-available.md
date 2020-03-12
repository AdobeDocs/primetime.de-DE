---
description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
seo-description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
seo-title: Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren
title: Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren
uuid: 637a70c9-9bef-4b13-8b1f-62f22f983e80
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren{#select-a-current-caption-track-from-among-available-tracks}

Sie können eine Spur aus einer Liste von derzeit verfügbaren Untertitelspuren auswählen. Dies wird zur aktuellen Spur, die angezeigt wird, wenn die Sichtbarkeit aktiviert ist. Einige Tracks sind möglicherweise nicht verfügbar, also suchen Sie nach dem Ereignis, das anzeigt, dass mehr verfügbar sind.

>[!TIP]
>
>Untertitel sind immer aktiviert. Alle standardmäßigen Untertitelspuren gelten als vorhanden. Standardspuren (z. B. CC1-CC4, CS1-CS6) werden in aufgezählt `ClosedCaptionsTrack.DefaultCCTypes`. Wenn die Wiedergabe beginnt, sucht TVSDK auf einem dieser Kanal nach Aktivität. Wenn er Aktivität findet, legt er die `isActive` Methode für diese Verfolgung fest und löst das `MediaPlayer.PlaybackEventListener.onUpdated` Ereignis aus.

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
   
<b>mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track);</b>
selectedClosedCaptionsIndex = i;
}}

```
1. Implement a listener for the event that indicates that more tracks are available. When TVSDK dispatches the event, retrieve the current list of available tracks.

Retrieve the list each time that the event occurs to ensure that you always have the most current list.

