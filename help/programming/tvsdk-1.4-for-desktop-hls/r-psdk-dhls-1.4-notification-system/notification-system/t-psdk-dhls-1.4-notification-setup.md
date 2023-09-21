---
description: Sie können Benachrichtigungen überwachen und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.
title: Benachrichtigungssystem einrichten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Benachrichtigungssystem einrichten{#set-up-your-notification-system}

Sie können Benachrichtigungen überwachen und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.

Der Kern des Primetime-Player-Benachrichtigungssystems ist die Benachrichtigungsklasse, die eine eigenständige Benachrichtigung darstellt.

Die NotificationHistory -Klasse bietet einen Mechanismus zum Ansammeln von Benachrichtigungen. Es speichert ein Benachrichtigungsprotokoll ( `NotificationHistoryItem`) Objekte, die eine Sammlung von Benachrichtigungen darstellen.

Benachrichtigungen erhalten:

* Benachrichtigungen abrufen
* Hinzufügen von Benachrichtigungen zum Benachrichtigungsverlauf

1. Suchen Sie nach Statusänderungen.
1. Implementieren des `MediaPlayer.StatusChangeEvent.STATUS_CHANGED` Ereignis-Listener.
1. TVSDK übergibt eine `MediaPlayer.StatusChangeEvent` -Instanz zum Ereignis-Listener, der zwei Parameter enthält:

   * Der neue Status ( `MediaPlayer.Status`)
   * A `MediaPlayerNotification` Objekt
