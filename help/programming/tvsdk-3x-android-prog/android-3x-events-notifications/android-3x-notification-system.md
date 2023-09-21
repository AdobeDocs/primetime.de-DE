---
description: Mit Ereignissen und Benachrichtigungen können Sie die asynchronen Aspekte der Videoanwendung verwalten.
title: Benachrichtigungen und Ereignisse für Player-Status, -Aktivität, Fehler und Protokollierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# Benachrichtigungen und Ereignisse für Player-Status, -Aktivität, Fehler und Protokollierung {#notifications-and-events-for-player-status-activity-errors-and-logging}

Mit Ereignissen und Benachrichtigungen können Sie die asynchronen Aspekte der Videoanwendung verwalten.

`MediaPlayerStatus` -Objekte enthalten Informationen zu Änderungen des Player-Status. `Notification` -Objekte enthalten Informationen zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players. Sie implementieren Ereignis-Listener, um Ereignisse zu erfassen und darauf zu reagieren ( `MediaPlayerEvent` -Objekte).

Ihre Anwendung kann Benachrichtigungen und Statusinformationen abrufen. Mithilfe dieser Informationen können Sie auch ein Protokollierungssystem für Diagnose und Validierung erstellen.

## Benachrichtigungsinhalt {#section_DF951FF601794CF592841BB7406DC1A1}

`MediaPlayerNotification` enthält Informationen zum Status des Players.

TVSDK bietet eine chronologische Liste von `MediaPlayerNotification` Benachrichtigungen und jede Benachrichtigung enthält die folgenden Informationen:

* Ein Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * `type`: INFO, WARN oder FEHLER.
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Benachrichtigung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel-Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Beispiel: ein Schlüssel mit dem Namen `URL` stellt einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf einen anderen `MediaPlayerNotification` -Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen lokal zur späteren Analyse speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.

## Benachrichtigungssystem einrichten {#section_9E37C09ECFA54B3DA8D3AA9ED1BAFC17}

Sie können Benachrichtigungen überwachen.

Der Kern des Primetime Player-Benachrichtigungssystems ist der `Notification` -Klasse, die eine eigenständige Benachrichtigung darstellt.

Um Benachrichtigungen zu erhalten, warten Sie wie folgt auf Benachrichtigungen:

1. Implementieren des `NotificationEventListener.onNotification()` Callback.
1. TVSDK übergibt eine `NotificationEvent` -Objekt auf den Rückruf zurück.

   >[!NOTE]
   >
   >Die Benachrichtigungstypen werden im Abschnitt `Notification.Type` enum:

   * `ERROR`
   * `INFO`
   * `WARNING`

## Echtzeit-Protokollierung und -Debugging hinzufügen {#section_9D4004308CB243AD9B50818895D10005}

Sie können Benachrichtigungen verwenden, um die Echtzeit-Protokollierung in Ihrer Videoanwendung zu implementieren.

Mit dem Benachrichtigungssystem können Sie Protokollierungs- und Debugging-Informationen für Diagnose und Validierung erfassen, ohne das System zu belasten.

>[!IMPORTANT]
>
>Das Protokollierungs-Backend ist nicht Teil eines Produktions-Setups und wird voraussichtlich nicht mit hohem Traffic verarbeitet. Wenn Ihre Implementierung nicht vollständig sein muss, sollten Sie die Effizienz der Datenübertragung berücksichtigen, um eine Überlastung Ihres Systems zu vermeiden.

Im Folgenden finden Sie ein Beispiel für den Abruf von Benachrichtigungen:

1. Erstellen Sie einen Timer-basierten Ausführungs-Thread für Ihre Videoanwendung, der regelmäßig die vom TVSDK-Benachrichtigungssystem erfassten Daten abfragt.
1. Wenn das Intervall des Timers zu groß ist und die Größe der Ereignisliste zu klein ist, wird die Benachrichtigungs-Ereignisliste überlaufen.

   >[!NOTE]
   >
   >Um diesen Überlauf zu vermeiden, führen Sie einen der folgenden Schritte aus:
   >
   >1. Verringern Sie das Zeitintervall, das den Thread steuert, der nach neuen Ereignissen abfragt.
   >
   >1. Vergrößern Sie die Benachrichtigungsliste.

1. Serialisieren Sie die neuesten Benachrichtigungsereigniseinträge im JSON-Format und senden Sie die Einträge zur Nachbearbeitung an einen Remote-Server.

   >[!NOTE]
   >
   >Der Remote-Server kann die bereitgestellten Daten grafisch in Echtzeit anzeigen.

1. Um den Verlust von Benachrichtigungsereignissen zu erkennen, suchen Sie nach Lücken in der Reihenfolge der Ereignisindexwerte.
