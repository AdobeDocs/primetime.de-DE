---
description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
title: Auf gültigen Status warten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Auf gültigen Status warten {#wait-for-a-valid-status}

Mit TVSDK können Sie das grundlegende Wiedergabeerlebnis für Live- und Video On Demand (VOD) steuern. TVSDK stellt Methoden und Eigenschaften in der Player-Instanz bereit, die Sie zum Konfigurieren der Player-Benutzeroberfläche verwenden können.

Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Wenn darauf gewartet wird, dass der Player den richtigen Status aufweist, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn der Player nicht mindestens den erforderlichen Status aufweist, werden von vielen Player-Methoden `MediaPlayerException`.

Der erforderliche Status ist normalerweise VORBEREITT. In diesem Fall wird die Callback-Routine für `StatusChangeEventListener.onStatusChanged()` wird ausgeführt.

So bestätigen Sie den Status `PREPARED`, check `MediaPlayer.MediaPlayerStatus`.
