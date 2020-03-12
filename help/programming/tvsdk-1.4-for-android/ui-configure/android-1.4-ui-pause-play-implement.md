---
description: Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
seo-description: Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
seo-title: Video abspielen und anhalten
title: Video abspielen und anhalten
uuid: 24b26364-5cb8-4a95-9574-cc52ddfa876b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Video abspielen und anhalten{#play-and-pause-a-video}

Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.

1. Erstellen Sie eine Pause-/Wiedergabeschaltfläche, die Folgendes ausführt:
   1. Warten Sie, bis Ihr Spieler mindestens den Status VORBEREITT hat.
   1. Rufen Sie zur Wiedergabe des Beginns die TVSDK-Wiedergabemethode auf:

      ```java
      void play() throws IllegalStateException;
      ```

   1. Rufen Sie zum Anhalten der Wiedergabe die TVSDK-Pausenmethode auf:

      ```java
      void pause() throws IllegalStateException;
      ```

1. Verwenden Sie den `MediaPlayer.PlaybackEventListener.onStateChanged` Rückruf, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   TVSDK ruft diesen Rückruf auf, wenn die Pause- oder play-Methode aufgerufen wird. TVSDK übergibt Informationen zur Statusänderung im Rückruf, einschließlich des neuen Status, wie PAUSED oder PLAYING.

