---
description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.
seo-description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.
seo-title: Benachrichtigungsklassen
title: Benachrichtigungsklassen
uuid: 08c29efe-245d-4a6d-80c6-cd561cbf3b5f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Benachrichtigungsklassen{#notification-classes}

Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.

| Klassenname | Beschreibung |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Klasse, die die Benachrichtigung für einen Fehler beschreibt, der dazu führt, dass der Player die Wiedergabe stoppt. Dies ist eine [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) des Benachrichtigungstyps ERROR. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Liste aller vom Primetime Player-Framework ausgelösten Benachrichtigungen. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Klasse, die Informationsmeldungen, Warnungen und Fehler bereitstellt. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungs-Ereignisses in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Klasse, die ein Protokoll der Benachrichtigungsobjekte [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) -Objekte speichert, die Zugriff auf die Liste des Benachrichtigungsverlaufs für Ereignis bieten. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz der [PTNotification enthält.](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Klasse, die einen Eintrag in der zirkulären Liste in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) definiert und die Benachrichtigung und ihren Zeitstempel enthält. |

