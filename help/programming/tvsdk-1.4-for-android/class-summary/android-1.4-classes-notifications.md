---
description: Diese Klassen beschreiben Meldungen über Fehler, Warnungen und einige Aktivitäten, die das TVSDK für Protokollierungs- und Debugging-Zwecke ausgibt.
title: Benachrichtigungsklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Benachrichtigungsklassen{#notification-classes}

Diese Klassen beschreiben Meldungen über Fehler, Warnungen und einige Aktivitäten, die das TVSDK für Protokollierungs- und Debugging-Zwecke ausgibt.

Package: [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html)  Package: [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| Klassenname | Beschreibung |
|---|---|
| MediaPlayerNotification. [Fehler](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | Klasse, die die Benachrichtigung für einen Fehler beschreibt, der dazu führt, dass der Player die Wiedergabe stoppt. Dies ist ein [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) des Meldetyps ERROR. |
| MediaPlayerNotification. [Info](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | Klasse, die eine Informationsbenachrichtigung beschreibt. Dies ist ein [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) des Meldetyps INFO. |
| MediaPlayerNotification. [Warnung](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | Klasse, die eine Warnmeldung beschreibt. Dies ist ein [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) des Benachrichtigungstyps WARNUNG. |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | Klasse mit Informationsmeldungen, Warnungen und Fehlern. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungsereignisses in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html). |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | Gibt die mit dem angegebenen Benachrichtigungscode verknüpfte Beschreibung zurück. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | Klasse, die ein Protokoll von Benachrichtigungsobjekten speichert. Eine kreisförmige Liste von [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) -Objekte, die Zugriff auf die Verlaufsliste von Benachrichtigungsereignissen bieten. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz der [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) -Klasse. (in [session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html) Paket.) |
| NotificationHistory. [Posten](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | Klasse, die einen Eintrag in der kreisförmigen Liste in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) und enthält die Benachrichtigung und ihren Zeitstempel. |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | Klasse mit den unterstützten Benachrichtigungstypen. |
