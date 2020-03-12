---
description: Sie können Schaltflächen zum Anhalten und Abspielen hinzufügen, um das Video anzuhalten oder abzuspielen.
seo-description: Sie können Schaltflächen zum Anhalten und Abspielen hinzufügen, um das Video anzuhalten oder abzuspielen.
seo-title: Video abspielen und anhalten
title: Video abspielen und anhalten
uuid: 3778a1fb-929c-4579-a14c-561179473dea
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Video abspielen und anhalten {#play-and-pause-a-video}

Sie können Schaltflächen zum Anhalten und Abspielen hinzufügen, um das Video anzuhalten oder abzuspielen.

1. So erstellen Sie eine Pause- oder Abspielen-Schaltfläche:
   1. Warten Sie, bis der Spieler mindestens im vorbereiteten Zustand ist.
   1. Rufen Sie zur Wiedergabe des Beginns die `play` Methode auf:

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Rufen Sie zum Anhalten der Wiedergabe die `pause()` Methode auf:

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Verwenden Sie den Rückruf des Statusänderungs-Ereignisses, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   TVSDK ruft diesen Rückruf auf `pause()` oder `play()` gibt Informationen zur Statusänderung, einschließlich des neuen Status, z. B. angehalten oder abgespielt, weiter.