---
description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
seo-description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
seo-title: Warten auf gültigen Status
title: Warten auf gültigen Status
uuid: e13201d7-b217-4d01-bdb7-a71855e3500e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Warten auf gültigen Status{#wait-for-a-valid-state}

Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Der Player durchläuft verschiedene Status. Wenn Sie darauf warten, dass der Player den richtigen Status hat, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn sich der Player nicht in mindestens dem erforderlichen Status befindet, werden viele Player-Methoden ausgelöst `IllegalStateException`.

Der erforderliche Status ist in der Regel `PTMediaPlayerStatusReady`.
