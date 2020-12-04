---
description: Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
seo-description: Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
seo-title: Video abspielen und anhalten
title: Video abspielen und anhalten
uuid: 04b3b23f-5ef1-4cc4-a22f-f6ffa9cefce5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# Video{#play-and-pause-a-video} abspielen und anhalten

Sie können TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.

1. Erstellen Sie eine Pause-/Wiedergabeschaltfläche, die Folgendes ausführt:
   1. Warten Sie, bis Ihr Spieler mindestens den Status VORBEREITT hat.
   1. Rufen Sie zur Wiedergabe des Beginns die TVSDK-play-Methode auf:

      ```
      function play():void;
      ```

   1. Rufen Sie zum Anhalten der Wiedergabe die TVSDK-Pausenmethode auf:

      ```
      function pause():void;
      ```

1. Verwenden Sie den Rückruf für das `MediaPlayerStatusChangeEvent.STATUS_CHANGED`-Ereignis, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   TVSDK ruft diesen Rückruf auf, wenn die Pause- oder play-Methode aufgerufen wird. TVSDK gibt Informationen zur Statusänderung im Rückruf, einschließlich des neuen Status, wie PAUSED oder PLAYING, weiter.
