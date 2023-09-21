---
description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
title: Auf gültigen Status warten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Auf gültigen Status warten{#wait-for-a-valid-state}

Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Der Player durchläuft verschiedene Status. Wenn darauf gewartet wird, dass der Player den richtigen Status aufweist, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn der Player nicht mindestens den erforderlichen Status aufweist, werden von vielen Player-Methoden `IllegalStateException`.

Der erforderliche Status ist normalerweise `PTMediaPlayerStatusReady`.
