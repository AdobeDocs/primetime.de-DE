---
description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die beim Protokollieren und Debuggen auftreten.
seo-description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die beim Protokollieren und Debuggen auftreten.
seo-title: Benachrichtigungsklassen
title: Benachrichtigungsklassen
uuid: 3befc64b-4abd-47df-9c45-215b49029757
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Benachrichtigungsklassen {#notification-classes}

Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die beim Protokollieren und Debuggen auftreten.

Paket: [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Klassenname | Beschreibung |
|---|---|
| [Benachrichtigung](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Klasse, die Informationsmeldungen, Warnungen und Fehler bereitstellt. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungs-Ereignisses in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Gibt die mit dem angegebenen Benachrichtigungscode verknüpfte Beschreibung zurück und stellt numerische Konstanten für Benachrichtigungsobjekte bereit. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Klasse, die ein Protokoll von Benachrichtigungsobjekten speichert. Eine zirkuläre Liste von [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) -Objekten, die Zugriff auf eine Liste des Benachrichtigungs-Ereignisses-Verlaufs bietet. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz der [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) -Klasse enthält. |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Klasse, die einen Eintrag in der zirkulären Liste in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) definiert und die Benachrichtigung und ihren Zeitstempel speichert. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Klasse, die die unterstützten Benachrichtigungstypen enthält. |

