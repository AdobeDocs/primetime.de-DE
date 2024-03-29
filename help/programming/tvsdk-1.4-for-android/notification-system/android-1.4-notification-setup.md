---
description: Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.
title: Einrichten des Benachrichtigungssystems
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Einrichten des Benachrichtigungssystems{#set-up-your-notification-system}

Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.

Der Kern des Primetime Player-Benachrichtigungssystems ist die `Notification`-Klasse, die eine eigenständige Benachrichtigung darstellt.

Die `NotificationHistory`-Klasse stellt einen Mechanismus zum Akkumulieren von Benachrichtigungen bereit. Es speichert ein Protokoll von Benachrichtigungsobjekten (NotificationHistoryItem), das eine Sammlung von Benachrichtigungen darstellt.

So empfangen Sie Benachrichtigungen:

* Benachrichtigungen abrufen
* hinzufügen Benachrichtigungen zum Benachrichtigungsverlauf

1. Suchen Sie nach Statusänderungen.
1. Implementieren Sie den Rückruf `MediaPlayer.PlaybackEventListener.onStateChanged`.
1. TVSDK übergibt zwei Parameter an den Rückruf:

   * Der neue Status ( `MediaPlayer.PlayerState`)
   * Ein `MediaPlayerNotification`-Objekt

