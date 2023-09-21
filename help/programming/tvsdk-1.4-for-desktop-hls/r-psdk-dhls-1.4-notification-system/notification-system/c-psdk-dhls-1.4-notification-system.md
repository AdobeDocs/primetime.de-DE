---
description: MediaPlayerNotification -Objekte liefern Informationen zu Änderungen des Player-Status, von Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
title: Benachrichtigungen bezüglich Player-Status, Aktivität, Fehler und Protokollierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---

# Übersicht {#notifications-for-player-status-activity-errors-and-logging-overview}

MediaPlayerNotification -Objekte liefern Informationen zu Änderungen des Player-Status, von Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.

Ihre Anwendung kann die Benachrichtigung und Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für Diagnose und Validierung erstellen.

Sie implementieren Ereignis-Listener, um Ereignisse zu erfassen und darauf zu reagieren. Viele Ereignisse bieten `MediaPlayerNotification` Statusbenachrichtigungen.
