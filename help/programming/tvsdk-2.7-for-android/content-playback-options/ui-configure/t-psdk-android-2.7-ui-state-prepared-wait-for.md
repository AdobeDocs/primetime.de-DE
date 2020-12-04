---
description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
seo-description: Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.
seo-title: Warten auf gültigen Status
title: Warten auf gültigen Status
uuid: ffa63ad6-84d3-4eb2-aa99-026418d86528
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---


# Warten Sie auf einen gültigen Status {#wait-for-a-valid-state}

Mit TVSDK können Sie die grundlegende Wiedergabe von Live- und Video On Demand (VOD) steuern. TVSDK stellt Methoden und Eigenschaften für die Player-Instanz bereit, die Sie zum Konfigurieren der Player-Benutzeroberfläche verwenden können.

Bevor Sie die meisten TVSDK-Player-Methoden verwenden können, muss sich der Player in einem gültigen Status befinden.

Wenn Sie darauf warten, dass der Player den richtigen Status hat, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn sich der Player nicht in mindestens dem erforderlichen Status befindet, geben viele Player-Methoden `MediaPlayerException` aus.

Der erforderliche Status wird in der Regel VORBEREITT. In diesem Fall wird die Callback-Routine für `StatusChangeEventListener.onStatusChanged()` ausgeführt.

1. Um zu bestätigen, dass der Status `PREPARED` lautet, markieren Sie `MediaPlayer.MediaPlayerStatus`.
