---
description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
title: Warten auf gültigen Status
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Warten Sie auf einen gültigen Status {#wait-for-a-valid-state}

Mit TVSDK können Sie die grundlegende Wiedergabe von Live- und Video On Demand (VOD) steuern. TVSDK stellt Methoden und Eigenschaften für die Player-Instanz bereit, die Sie zum Konfigurieren der Player-Benutzeroberfläche verwenden können. Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Der Player durchläuft verschiedene Status. Wenn Sie darauf warten, dass der Player den richtigen Status hat, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn sich der Player nicht in mindestens dem erforderlichen Status befindet, geben viele Player-Methoden throw `IllegalStateException` aus.

Der erforderliche Status wird in der Regel VORBEREITT.

1. So bestätigen Sie, dass der Status VORBEREITET ist:

   Wenn der Player initialisiert wird, warten Sie, bis TVSDK den Rückruf für das `MediaPlayerStatusChangeEvent.STATUS_CHANGED`-Ereignis mit VORBEREITENDEM Status aufruft.

   So prüfen Sie, ob der aktuelle Status des Objekts `MediaPlayer` mindestens VORBEREITET ist.

   ```
   function getstatus():String;
   ```
