---
description: Diese Klassen beschreiben Meldungen über Fehler, Warnungen und einige Aktivitäten, die die Probleme zu Protokollierungs- und Debugging-Zwecken betreffen.
title: Benachrichtigungsklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Benachrichtigungsklassen {#notification-classes}

Diese Klassen beschreiben Meldungen über Fehler, Warnungen und einige Aktivitäten, die die Probleme zu Protokollierungs- und Debugging-Zwecken betreffen.

Package: [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Klassenname | Beschreibung |
|---|---|
| [Benachrichtigung](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Klasse mit Informationsmeldungen, Warnungen und Fehlern. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungsereignisses in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Gibt die Beschreibung zurück, die mit dem bereitgestellten Benachrichtigungscode verknüpft ist, und stellt numerische Konstanten für Benachrichtigungsobjekte bereit. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Klasse, die ein Protokoll von Benachrichtigungsobjekten speichert. Eine kreisförmige Liste von [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) -Objekte, die Zugriff auf die Verlaufsliste von Benachrichtigungsereignissen bieten. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz der [Benachrichtigung](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) -Klasse. |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Klasse, die einen Eintrag in der kreisförmigen Liste in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) und enthält die Benachrichtigung und ihren Zeitstempel. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Klasse mit den unterstützten Benachrichtigungstypen. |
