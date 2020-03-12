---
description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.
seo-description: Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.
seo-title: Benachrichtigungsklassen
title: Benachrichtigungsklassen
uuid: e231a2d0-6190-4251-87db-ca46d2aee60d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Benachrichtigungsklassen{#notification-classes}

Diese Klassen beschreiben Fehlermeldungen, Warnungen und einige Aktivitäten, die das TVSDK zum Protokollieren und Debuggen ausgibt.

Paket: [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html) Package: [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| Klassenname | Beschreibung |
|---|---|
| MediaPlayerNotification. [Fehler](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | Klasse, die die Benachrichtigung für einen Fehler beschreibt, der dazu führt, dass der Player die Wiedergabe stoppt. Dies ist eine [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) des Benachrichtigungstyps ERROR. |
| MediaPlayerNotification. [Info](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | Klasse, die eine Informationsbenachrichtigung beschreibt. Dies ist eine [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) des Benachrichtigungstyps INFO. |
| MediaPlayerNotification. [Warnung](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | Klasse, die eine Warnmeldung beschreibt. Dies ist eine [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) des Benachrichtigungstyps WARNUNG. |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | Klasse, die Informationsmeldungen, Warnungen und Fehler bereitstellt. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungs-Ereignisses in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html). |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | Gibt die mit dem angegebenen Benachrichtigungscode verknüpfte Beschreibung zurück. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | Klasse, die ein Protokoll von Benachrichtigungsobjekten speichert. Eine zirkuläre Liste von [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) -Objekten, die Zugriff auf die Liste des Benachrichtigungs-Ereignisses-Verlaufs bietet. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz der [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) -Klasse enthält. (Im [Sitzungspaket](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html) .) |
| NotificationHistory. [Posten](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | Klasse, die einen Eintrag in der zirkulären Liste in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) definiert und die Benachrichtigung und ihren Zeitstempel speichert. |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | Klasse, die die unterstützten Benachrichtigungstypen enthält. |