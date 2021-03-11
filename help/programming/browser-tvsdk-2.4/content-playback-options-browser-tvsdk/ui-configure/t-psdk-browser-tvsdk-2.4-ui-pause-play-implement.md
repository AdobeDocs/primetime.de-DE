---
description: Sie können Browser TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
title: Video abspielen und anhalten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Video{#play-and-pause-a-video} abspielen und anhalten

Sie können Browser TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.

1. Erstellen Sie eine Pause-/Wiedergabeschaltfläche, die Folgendes ausführt:
   1. Warten Sie, bis Ihr Spieler mindestens den Status VORBEREITT hat.
   1. Rufen Sie zur Wiedergabe des Beginns die Browser TVSDK-Wiedergabemethode auf:

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. Um die Wiedergabe anzuhalten, rufen Sie die Browser TVSDK-Pausenmethode auf:

      ```java
      void pause() throws IllegalStateException;
      ```

1. Suchen Sie nach dem `AdobePSDK.MediaPlayerStatusChangeEvent`-Ereignis, um nach Fehlern zu suchen oder andere geeignete Maßnahmen zu ergreifen.

   Browser TVSDK Trigger dieses Ereignis, wenn Pause- oder Wiedergabemethoden aufgerufen werden, und gibt Informationen zum Ereignis-Objekt, einschließlich des neuen Status, wie `MediaPlayerStatus.PLAYING` oder `MediaPlayerStatus.PAUSED` weiter.

