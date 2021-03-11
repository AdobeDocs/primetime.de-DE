---
description: Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
title: Video abspielen und anhalten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Video{#play-and-pause-a-video} abspielen und anhalten

Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.

1. Erstellen Sie eine Pause-/Wiedergabeschaltfläche, die Folgendes ausführt:
   1. Warten Sie, bis Ihr Spieler mindestens den Status VORBEREITT hat.
   1. Rufen Sie zur Wiedergabe des Beginns die TVSDK-Wiedergabemethode auf:

      ```
      function play():void;
      ```

   1. Rufen Sie zum Anhalten der Wiedergabe die TVSDK-Pausenmethode auf:

      ```
      function pause():void;
      ```

1. Verwenden Sie den Rückruf für das `MediaPlayerStatusChangeEvent.STATUS_CHANGED`-Ereignis, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   TVSDK ruft diesen Rückruf auf, wenn die Pause- oder play-Methode aufgerufen wird. TVSDK gibt Informationen zur Statusänderung im Rückruf, einschließlich des neuen Status, wie PAUSED oder PLAYING, weiter.
