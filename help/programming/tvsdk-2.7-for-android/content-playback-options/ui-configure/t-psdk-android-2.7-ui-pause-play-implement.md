---
description: Sie können Schaltflächen zum Anhalten und Abspielen hinzufügen, um das Video anzuhalten oder abzuspielen.
seo-description: Sie können Schaltflächen zum Anhalten und Abspielen hinzufügen, um das Video anzuhalten oder abzuspielen.
seo-title: Video abspielen und anhalten
title: Video abspielen und anhalten
uuid: 66fefead-7f1d-46ed-a23e-381f25697978
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

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

