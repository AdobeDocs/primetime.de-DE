---
description: Sie können Browser TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
seo-description: Sie können Browser TVSDK-Verhalten hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
seo-title: Video abspielen und anhalten
title: Video abspielen und anhalten
uuid: 4053ea9e-6b74-41e9-ad04-087ad13e3698
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '127'
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

   Browser TVSDK löst dieses Ereignis aus, wenn Pause- oder Wiedergabemethoden aufgerufen werden, und gibt Informationen zum Ereignis-Objekt, einschließlich des neuen Status, wie `MediaPlayerStatus.PLAYING` oder `MediaPlayerStatus.PAUSED` weiter.

