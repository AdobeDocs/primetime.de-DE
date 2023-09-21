---
description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
title: Auf gültigen Status warten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Auf gültigen Status warten {#wait-for-a-valid-state}

Mit TVSDK können Sie das grundlegende Wiedergabeerlebnis für Live- und Video On Demand (VOD) steuern. TVSDK stellt Methoden und Eigenschaften in der Player-Instanz bereit, die Sie zum Konfigurieren der Player-Benutzeroberfläche verwenden können. Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Der Player durchläuft verschiedene Status. Wenn darauf gewartet wird, dass der Player den richtigen Status aufweist, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn der Player nicht mindestens den erforderlichen Status aufweist, werfen viele Player-Methoden `IllegalStateException`.

Der erforderliche Status ist normalerweise VORBEREITT.

1. So bestätigen Sie, dass der Status VORBEREITET ist:

   Wenn der Player initialisiert wird, warten Sie, bis TVSDK den Callback für die `MediaPlayerStatusChangeEvent.STATUS_CHANGED` -Ereignis mit dem Status VORBEREITET .

   So prüfen Sie, ob der aktuelle Status der `MediaPlayer` -Objekt zumindest VORBEREITET ist.

   ```
   function getstatus():String;
   ```
