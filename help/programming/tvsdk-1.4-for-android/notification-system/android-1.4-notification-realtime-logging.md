---
description: Sie können Benachrichtigungen verwenden, um die Echtzeit-Anmeldung in Ihrer Videoanwendung zu implementieren.
seo-description: Sie können Benachrichtigungen verwenden, um die Echtzeit-Anmeldung in Ihrer Videoanwendung zu implementieren.
seo-title: Hinzufügen Echtzeit-Protokollierung und -Debugging
title: Hinzufügen Echtzeit-Protokollierung und -Debugging
uuid: 037daf57-a1b3-4b42-ac51-81179fb36915
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Hinzufügen Echtzeit-Protokollierung und -Debugging{#add-real-time-logging-and-debugging}

Sie können Benachrichtigungen verwenden, um die Echtzeit-Anmeldung in Ihrer Videoanwendung zu implementieren.

Mit dem Benachrichtigungssystem können Sie Protokollierungs- und Debugging-Informationen für die Diagnose und Validierung erfassen, ohne das System übermäßig zu belasten.

>[!IMPORTANT]
>
>Das Back-End für die Protokollierung ist nicht Teil eines Produktions-Setups und wird voraussichtlich nicht mit hohem Traffic verarbeitet. Wenn Ihre Implementierung nicht vollständig sein muss, sollten Sie die Effizienz der Datenübertragung berücksichtigen, um eine Überlastung Ihres Systems zu vermeiden.

Im Folgenden finden Sie ein Beispiel zum Abrufen von Benachrichtigungen.

1. Erstellen Sie einen Timer-basierten Ausführungsthread für Ihre Videoanwendung, der die vom TVSDK-Benachrichtigungssystem erfassten Daten in regelmäßigen Abständen Abfrage.

1. Wenn das Zeitintervall zu groß ist und die Liste des Ereignisses zu klein ist, wird die Liste des Ereignisses für Benachrichtigungen überlaufen. Führen Sie einen der folgenden Schritte aus, um diesen Überlauf zu vermeiden:

   * Verringern Sie das Zeitintervall, das den Thread auslöst, der nach neuen Ereignissen fragt.
   * Vergrößern Sie die Benachrichtigungs-Liste.

1. Serialisieren Sie die neuesten Benachrichtigungs-Ereignis-Einträge im JSON-Format und senden Sie die Einträge zur Nachbearbeitung an einen Remoteserver.

   Der Remote-Server könnte dann die bereitgestellten Daten grafisch in Echtzeit anzeigen.
1. Um den Verlust von Benachrichtigungs-Ereignissen zu ermitteln, suchen Sie nach Lücken in der Sequenz von Ereignis-Indexwerten.

   Jedes Benachrichtigungs-Ereignis verfügt über einen Indexwert, der automatisch von der `session.NotificationHistory` Klasse inkrementiert wird.
