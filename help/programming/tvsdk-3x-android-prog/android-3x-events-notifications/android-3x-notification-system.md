---
description: Mithilfe von Ereignissen und Benachrichtigungen können Sie die asynchronen Aspekte der Videoanwendung verwalten.
seo-description: Mithilfe von Ereignissen und Benachrichtigungen können Sie die asynchronen Aspekte der Videoanwendung verwalten.
seo-title: Benachrichtigungen und Ereignis für Player-Status, Aktivität, Fehler und Protokollierung
title: Benachrichtigungen und Ereignis für Player-Status, Aktivität, Fehler und Protokollierung
uuid: c4a108e7-72aa-4c96-9538-b1385343d6af
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Benachrichtigungen und Ereignis für Player-Status, Aktivität, Fehler und Protokollierung {#notifications-and-events-for-player-status-activity-errors-and-logging}

Mithilfe von Ereignissen und Benachrichtigungen können Sie die asynchronen Aspekte der Videoanwendung verwalten.

`MediaPlayerStatus` Objekte enthalten Informationen zu Änderungen im Player-Status. `Notification` Objekte enthalten Informationen zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players. Sie implementieren Ereignis-Listener, um Ereignis ( `MediaPlayerEvent` Objekte) zu erfassen und darauf zu reagieren.

Ihre Anwendung kann Benachrichtigungen und Statusinformationen abrufen. Mithilfe dieser Informationen können Sie auch ein Protokollierungssystem für die Diagnose und Überprüfung erstellen.

## Benachrichtigungsinhalt {#section_DF951FF601794CF592841BB7406DC1A1}

`MediaPlayerNotification` enthält Informationen zum Status des Spielers.

TVSDK stellt eine chronologische Liste der `MediaPlayerNotification` Benachrichtigungen bereit. Jede Benachrichtigung enthält die folgenden Informationen:

* Ein Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * `type`: INFO, WARN oder FEHLER.
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Anmeldung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel/Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Ein Schlüssel mit dem Namen `URL` stellt beispielsweise einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf ein anderes `MediaPlayerNotification` Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen zur späteren Analyse lokal speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.

## Einrichten des Benachrichtigungssystems {#section_9E37C09ECFA54B3DA8D3AA9ED1BAFC17}

Sie können auf Benachrichtigungen warten.

Der Kern des Primetime Player-Benachrichtigungssystems ist die `Notification` Klasse, die eine eigenständige Benachrichtigung darstellt.

Um Benachrichtigungen zu erhalten, warten Sie wie folgt auf Benachrichtigungen:

1. Implementieren Sie den `NotificationEventListener.onNotification()` Rückruf.
1. TVSDK übergibt ein `NotificationEvent` Objekt an den Rückruf.

   >[!NOTE]
   >
   >Benachrichtigungstypen werden in der `Notification.Type` Enum aufgezählt:

   * `ERROR`
   * `INFO`
   * `WARNING`

## Hinzufügen Echtzeit-Protokollierung und -Debugging {#section_9D4004308CB243AD9B50818895D10005}

Sie können Benachrichtigungen verwenden, um die Echtzeit-Anmeldung in Ihrer Videoanwendung zu implementieren.

Mit dem Benachrichtigungssystem können Sie Protokollierungs- und Debugging-Informationen für die Diagnose und Validierung erfassen, ohne das System zu belasten.

>[!IMPORTANT]
>
>Das Back-End für die Protokollierung ist nicht Teil eines Produktions-Setups und wird voraussichtlich nicht mit hohem Traffic verarbeitet. Wenn Ihre Implementierung nicht vollständig sein muss, sollten Sie die Effizienz der Datenübertragung berücksichtigen, um eine Überlastung Ihres Systems zu vermeiden.

Im Folgenden finden Sie ein Beispiel zum Abrufen von Benachrichtigungen:

1. Erstellen Sie einen Timer-basierten Ausführungsthread für Ihre Videoanwendung, der die vom TVSDK-Benachrichtigungssystem erfassten Daten in regelmäßigen Abständen Abfrage.
1. Wenn das Zeitintervall zu groß ist und die Liste des Ereignisses zu klein ist, wird die Liste des Ereignisses für Benachrichtigungen überlaufen.

   >[!NOTE]
   >
   >Führen Sie einen der folgenden Schritte aus, um diesen Überlauf zu vermeiden:    >
   >    
   >    
   >    1. Verringern Sie das Zeitintervall, das den Thread auslöst, der nach neuen Ereignissen fragt.
   >    1. Vergrößern Sie die Benachrichtigungs-Liste.


1. Serialisieren Sie die neuesten Benachrichtigungs-Ereignis-Einträge im JSON-Format und senden Sie die Einträge zur Nachbearbeitung an einen Remoteserver.

   >[!NOTE]
   >
   >Der Remote-Server kann die bereitgestellten Daten grafisch in Echtzeit anzeigen.

1. Um den Verlust von Benachrichtigungs-Ereignissen zu ermitteln, suchen Sie nach Lücken in der Sequenz von Ereignis-Indexwerten.