---
description: Sie können das TVSDK-Verhalten hinzufügen, um die Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
title: Video abspielen und anhalten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Video abspielen und anhalten{#play-and-pause-a-video}

Sie können das TVSDK-Verhalten hinzufügen, um die Schaltflächen zum Anhalten und Abspielen hinzuzufügen.

1. Erstellen Sie eine Pause-/Play-Schaltfläche mit folgenden Funktionen.
   1. Warten Sie, bis Ihr Player mindestens den Status VORBEREITET aufweist.
   1. Rufen Sie zum Starten der Wiedergabe die TVSDK-Wiedergabemethode auf:

      ```
      function play():void;
      ```

   1. Um die Wiedergabe anzuhalten, rufen Sie die TVSDK-Pausenmethode auf:

      ```
      function pause():void;
      ```

1. Verwenden Sie den Rückruf für die `MediaPlayerStatusChangeEvent.STATUS_CHANGED` -Ereignis, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   TVSDK ruft diesen Rückruf auf, wenn die Methode zum Anhalten oder Abspielen aufgerufen wird. TVSDK gibt Informationen über die Statusänderung im Callback weiter, einschließlich des neuen Status, z. B. PAUSED oder PLAYING.
