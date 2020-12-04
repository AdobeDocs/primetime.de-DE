---
description: MediaPlayerNotification-Objekte enthalten Informationen zu Änderungen des Player-Status, zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
seo-description: MediaPlayerNotification-Objekte enthalten Informationen zu Änderungen des Player-Status, zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
seo-title: Benachrichtigungen über Player-Status, Aktivität, Fehler und Protokollierung
title: Benachrichtigungen über Player-Status, Aktivität, Fehler und Protokollierung
uuid: 7ce5bed0-f312-437e-a82f-b1d4a8e1926c
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Übersicht {#notifications-for-player-status-activity-errors-and-logging-overview}

MediaPlayerNotification-Objekte enthalten Informationen zu Änderungen des Player-Status, zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.

Ihre Anwendung kann die Benachrichtigungen und Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für die Diagnose und Überprüfung erstellen.

Sie implementieren Ereignis-Listener, um Ereignis zu erfassen und darauf zu reagieren. In vielen Ereignissen werden Statusbenachrichtigungen für `MediaPlayerNotification` bereitgestellt.