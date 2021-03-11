---
description: Bevor Sie die meisten Browser TVSDK Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
title: Warten auf gültigen Status
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Warten Sie auf einen gültigen Status {#wait-for-a-valid-state}

Bevor Sie die meisten Browser TVSDK Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Der Spieler durchläuft verschiedene Status. Wenn Sie darauf warten, dass der Player den richtigen Status hat, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn sich der Player nicht in mindestens dem erforderlichen Status befindet, geben viele Player-Methoden `IllegalStateException` aus.

Der erforderliche Status wird in der Regel VORBEREITT.

1. So bestätigen Sie, dass der Status VORBEREITET ist:

   Wenn der Player initialisiert wird, warten Sie, bis Browser TVSDK das `AdobePSDK.MediaPlayerStatusChangeEvent`-Ereignis mit einem `event.status` von `MediaPlayerStatus.PREPARED` auslöst.

   So prüfen Sie, ob der aktuelle Status des MediaPlayer-Objekts mindestens VORBEREITET ist.

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```

