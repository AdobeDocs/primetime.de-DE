---
description: Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.
seo-description: Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.
seo-title: Einrichten des Benachrichtigungssystems
title: Einrichten des Benachrichtigungssystems
uuid: 2d1876c7-4ce6-491c-880b-dd94697d4feb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Einrichten des Benachrichtigungssystems{#set-up-your-notification-system}

Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.

Der Kern des Primetime Player-Benachrichtigungssystems ist die Notification-Klasse, die eine eigenständige Benachrichtigung darstellt.

Die NotificationHistory-Klasse stellt einen Mechanismus zum Akkumulieren von Benachrichtigungen bereit. Es speichert ein Protokoll von Benachrichtigungsobjekten ( `NotificationHistoryItem`), das eine Sammlung von Benachrichtigungen darstellt.

So empfangen Sie Benachrichtigungen:

* Benachrichtigungen abrufen
* Hinzufügen Benachrichtigungen zum Benachrichtigungsverlauf

1. Suchen Sie nach Statusänderungen.
1. Implementieren Sie den `MediaPlayer.StatusChangeEvent.STATUS_CHANGED` Ereignis-Listener.
1. TVSDK übergibt eine `MediaPlayer.StatusChangeEvent` Instanz an den Ereignis-Listener, der zwei Parameter enthält:

   * Der neue Status ( `MediaPlayer.Status`)
   * Ein `MediaPlayerNotification` Objekt

