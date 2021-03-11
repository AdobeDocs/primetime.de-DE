---
description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die beim Protokollieren und Debuggen auftreten.
title: Benachrichtigungsklassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Benachrichtigungsklassen {#notification-classes}

Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die beim Protokollieren und Debuggen auftreten.

Paket: [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Klassenname | Beschreibung |
|---|---|
| [Benachrichtigung](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Klasse, die Informationsmeldungen, Warnungen und Fehler bereitstellt. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungs-Ereignisses innerhalb von [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Gibt die mit dem angegebenen Benachrichtigungscode verknüpfte Beschreibung zurück und stellt numerische Konstanten für Benachrichtigungsobjekte bereit. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Klasse, die ein Protokoll von Benachrichtigungsobjekten speichert. Eine zirkuläre Liste von [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html)-Objekten, die Zugriff auf eine Liste des Benachrichtigungs-Ereignisses-Verlaufs bietet. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz der Klasse [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) enthält. |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Klasse, die einen Eintrag in der kreisförmigen Liste in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) definiert und die Benachrichtigung und den zugehörigen Zeitstempel enthält. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Klasse, die die unterstützten Benachrichtigungstypen enthält. |

