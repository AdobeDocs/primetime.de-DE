---
description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
seo-description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
seo-title: Warten auf gültigen Status
title: Warten auf gültigen Status
uuid: 7a86b4cf-f7a0-4d90-9ff2-401640a395c5
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Warten auf gültigen Status {#wait-for-a-valid-status}

Mit TVSDK können Sie die grundlegende Wiedergabe von Live- und Video On Demand (VOD) steuern. TVSDK stellt Methoden und Eigenschaften für die Player-Instanz bereit, die Sie zum Konfigurieren der Player-Benutzeroberfläche verwenden können.

Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Wenn Sie darauf warten, dass der Player den richtigen Status hat, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn sich der Player nicht in mindestens dem erforderlichen Status befindet, werden viele Player-Methoden ausgelöst `MediaPlayerException`.

Der erforderliche Status wird in der Regel VORBEREITT. In diesem Fall wird die Callback-Routine für die `StatusChangeEventListener.onStatusChanged()` Ausführung ausgeführt.

Um zu bestätigen, dass der Status vorliegt, `PREPARED`überprüfen Sie `MediaPlayer.MediaPlayerStatus`.