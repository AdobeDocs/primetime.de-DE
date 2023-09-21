---
description: Sie können das Verhalten von Browser TVSDK hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.
title: Video abspielen und anhalten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Video abspielen und anhalten{#play-and-pause-a-video}

Sie können das Verhalten von Browser TVSDK hinzufügen, um Schaltflächen zum Anhalten und Abspielen hinzuzufügen.

1. Erstellen Sie eine Pause-/Play-Schaltfläche mit folgenden Funktionen.
   1. Warten Sie, bis Ihr Player mindestens den Status VORBEREITET aufweist.
   1. Um die Wiedergabe zu starten, rufen Sie die Browser TVSDK-Wiedergabemethode auf:

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. Um die Wiedergabe anzuhalten, rufen Sie die Methode &quot;Browser TVSDK pause&quot;auf:

      ```java
      void pause() throws IllegalStateException;
      ```

1. Suchen Sie nach `AdobePSDK.MediaPlayerStatusChangeEvent` -Ereignis, um nach Fehlern zu suchen oder andere geeignete Aktionen durchzuführen.

   Browser TVSDK Trigger dieses Ereignis beim Aufruf der Pause- oder Wiedergabemethoden und Übergibt Informationen zum Ereignisobjekt, einschließlich des neuen Status, z. B. `MediaPlayerStatus.PLAYING` oder `MediaPlayerStatus.PAUSED`.
