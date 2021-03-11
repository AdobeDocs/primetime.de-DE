---
description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.
title: Benachrichtigungsklassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Benachrichtigungsklassen {#notification-classes}

Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.

| **Klassenname** | **Beschreibung** |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Klasse, die die Benachrichtigung für einen Fehler beschreibt, der dazu führt, dass der Player die Wiedergabe stoppt. Dies ist eine [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) des Benachrichtigungstyps ERROR. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Liste aller vom Primetime Player-Framework ausgelösten Benachrichtigungen. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Klasse, die Informationsmeldungen, Warnungen und Fehler bereitstellt. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungs-Ereignisses innerhalb von [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Klasse, die ein Protokoll von Benachrichtigungsobjekten [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html)-Objekten speichert, die Zugriff auf die Liste des Benachrichtigungs-Ereignisses-Verlaufs bieten. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz von [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) enthält. |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Klasse, die einen Eintrag in der kreisförmigen Liste in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) definiert und die Benachrichtigung und den zugehörigen Zeitstempel enthält. |

