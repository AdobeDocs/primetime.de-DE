---
description: Bevor Sie die meisten Browser TVSDK-Player-Methoden verwenden können, muss der Player einen gültigen Status aufweisen.
title: Auf gültigen Status warten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Auf gültigen Status warten {#wait-for-a-valid-state}

Bevor Sie die meisten Browser TVSDK-Player-Methoden verwenden können, muss der Player einen gültigen Status aufweisen.

Der Player durchläuft verschiedene Status. Wenn darauf gewartet wird, dass der Player den richtigen Status aufweist, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn der Player nicht mindestens den erforderlichen Status aufweist, werden bei vielen Player-Methoden `IllegalStateException`.

Der erforderliche Status wird normalerweise VORBEREITT.

1. So bestätigen Sie, dass der Status VORBEREITET ist:

   Wenn der Player initialisiert wird, warten Sie, bis Browser TVSDK den `AdobePSDK.MediaPlayerStatusChangeEvent` -Ereignis mit einer `event.status` von `MediaPlayerStatus.PREPARED`.

   So überprüfen Sie, ob der aktuelle Status des MediaPlayer-Objekts mindestens VORBEREITET ist.

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```
