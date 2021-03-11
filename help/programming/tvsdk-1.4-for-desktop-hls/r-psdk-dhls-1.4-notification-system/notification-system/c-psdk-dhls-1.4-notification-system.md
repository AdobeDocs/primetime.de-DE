---
description: MediaPlayerNotification-Objekte enthalten Informationen zu Änderungen des Player-Status, zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
title: Benachrichtigungen über Player-Status, Aktivität, Fehler und Protokollierung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---


# Übersicht {#notifications-for-player-status-activity-errors-and-logging-overview}

MediaPlayerNotification-Objekte enthalten Informationen zu Änderungen des Player-Status, zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.

Ihre Anwendung kann die Benachrichtigungen und Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für die Diagnose und Überprüfung erstellen.

Sie implementieren Ereignis-Listener, um Ereignis zu erfassen und darauf zu reagieren. In vielen Ereignissen werden Statusbenachrichtigungen für `MediaPlayerNotification` bereitgestellt.