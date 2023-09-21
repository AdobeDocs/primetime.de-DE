---
description: Diese Klassen beschreiben Meldungen über Fehler, Warnungen und einige Aktivitäten, die das TVSDK für Protokollierungs- und Debugging-Zwecke ausgibt.
title: Benachrichtigungsklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Benachrichtigungsklassen{#notification-classes}

Diese Klassen beschreiben Meldungen über Fehler, Warnungen und einige Aktivitäten, die das TVSDK für Protokollierungs- und Debugging-Zwecke ausgibt.

| Klassenname | Beschreibung |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Klasse, die die Benachrichtigung für einen Fehler beschreibt, der dazu führt, dass der Player die Wiedergabe stoppt. Dies ist ein [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) des Meldetyps ERROR. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Listet alle Benachrichtigungen auf, die vom Primetime Player-Framework gesendet werden. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Klasse mit Informationsmeldungen, Warnungen und Fehlern. Kapselt die Objektdarstellung eines einzelnen Benachrichtigungsereignisses in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Klasse, die ein Protokoll von Benachrichtigungsobjekten speichert [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) -Objekte, die Zugriff auf die Verlaufsliste von Benachrichtigungsereignissen bieten. Das heißt, es behält eine Liste von Elementen bei, wobei jedes Element eine separate Instanz der [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Klasse, die einen Eintrag in der kreisförmigen Liste in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) und enthält die Benachrichtigung und ihren Zeitstempel. |
