---
description: Sie können das TVSDK-Verhalten hinzufügen, um die Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
title: Video abspielen und anhalten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Video abspielen und anhalten{#play-and-pause-a-video}

Sie können das TVSDK-Verhalten hinzufügen, um die Schaltflächen zum Anhalten und Abspielen hinzuzufügen.

1. Erstellen Sie eine Pause-/Play-Schaltfläche mit folgenden Funktionen.
   1. Warten Sie, bis Ihr Player mindestens den Status VORBEREITET aufweist.
   1. Rufen Sie zum Starten der Wiedergabe die TVSDK-Wiedergabemethode auf:

      ```java
      void play() throws IllegalStateException;
      ```

   1. Um die Wiedergabe anzuhalten, rufen Sie die TVSDK-Pausenmethode auf:

      ```java
      void pause() throws IllegalStateException;
      ```

1. Verwenden Sie die `MediaPlayer.PlaybackEventListener.onStateChanged` Callback, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   TVSDK ruft diesen Rückruf auf, wenn die Methode zum Anhalten oder Abspielen aufgerufen wird. TVSDK übergibt Informationen über die Statusänderung im Rückruf, einschließlich des neuen Status, z. B. &quot;PAUSED&quot;oder &quot;PLAYING&quot;.
