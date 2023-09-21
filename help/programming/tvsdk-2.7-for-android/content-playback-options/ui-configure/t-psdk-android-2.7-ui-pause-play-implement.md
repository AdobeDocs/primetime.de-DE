---
description: Sie können Schaltflächen zum Anhalten und Abspielen hinzufügen, um das Video anzuhalten oder wiederzugeben.
title: Video abspielen und anhalten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Video abspielen und anhalten {#play-and-pause-a-video}

Sie können Schaltflächen zum Anhalten und Abspielen hinzufügen, um das Video anzuhalten oder wiederzugeben.

1. So erstellen Sie eine Pause- oder Play-Schaltfläche:
   1. Warten Sie, bis der Player mindestens den vorbereiteten Status aufweist.
   1. Um die Wiedergabe zu starten, rufen Sie die `play` -Methode:

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Um die Wiedergabe anzuhalten, rufen Sie die `pause()` -Methode:

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Verwenden Sie den Rückruf Ereignis &quot;Status geändert&quot;, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   TVSDK ruft diesen Rückruf für `pause()` oder `play()` und gibt Informationen über die Statusänderung weiter, einschließlich des neuen Status, z. B. angehalten oder wiedergegeben.
