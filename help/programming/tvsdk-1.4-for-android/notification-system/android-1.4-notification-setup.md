---
description: Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.
seo-description: Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.
seo-title: Einrichten des Benachrichtigungssystems
title: Einrichten des Benachrichtigungssystems
uuid: caa6a306-dea9-45ee-b0b3-569b5f2527a1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Einrichten des Benachrichtigungssystems{#set-up-your-notification-system}

Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.

Der Kern des Primetime Player-Benachrichtigungssystems ist die `Notification` Klasse, die eine eigenständige Benachrichtigung darstellt.

Die `NotificationHistory` Klasse bietet einen Mechanismus zum Ansammeln von Benachrichtigungen. Es speichert ein Protokoll von Benachrichtigungsobjekten (NotificationHistoryItem), das eine Sammlung von Benachrichtigungen darstellt.

So empfangen Sie Benachrichtigungen:

* Benachrichtigungen abrufen
* Hinzufügen Benachrichtigungen zum Benachrichtigungsverlauf

1. Suchen Sie nach Statusänderungen.
1. Implementieren Sie den `MediaPlayer.PlaybackEventListener.onStateChanged` Rückruf.
1. TVSDK übergibt zwei Parameter an den Rückruf:

   * Der neue Status ( `MediaPlayer.PlayerState`)
   * Ein `MediaPlayerNotification` Objekt

