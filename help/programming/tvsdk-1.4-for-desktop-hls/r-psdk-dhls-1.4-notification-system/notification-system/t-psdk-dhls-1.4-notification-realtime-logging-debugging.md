---
description: Sie können Benachrichtigungen verwenden, um die Echtzeit-Protokollierung in Ihrer Videoanwendung zu implementieren.
title: Echtzeit-Protokollierung und -Debugging hinzufügen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Echtzeit-Protokollierung und -Debugging hinzufügen{#add-real-time-logging-and-debugging}

Sie können Benachrichtigungen verwenden, um die Echtzeit-Protokollierung in Ihrer Videoanwendung zu implementieren.

Mit dem Benachrichtigungssystem können Sie Protokollierungs- und Debugging-Informationen für Diagnose und Validierung erfassen, ohne das System übermäßig zu belasten.

>[!IMPORTANT]
>
>Das Protokollierungs-Backend ist nicht Teil eines Produktions-Setups und wird voraussichtlich nicht mit hohem Traffic verarbeitet. Wenn Ihre Implementierung nicht vollständig sein muss, sollten Sie die Effizienz der Datenübertragung berücksichtigen, um eine Überlastung Ihres Systems zu vermeiden.

Im Folgenden finden Sie ein Beispiel für den Abruf von Benachrichtigungen.

1. Erstellen Sie einen Timer-basierten Ausführungs-Thread für Ihre Videoanwendung, der regelmäßig die vom TVSDK-Benachrichtigungssystem erfassten Daten abfragt.

1. Wenn das Intervall des Timers zu groß ist und die Größe der Ereignisliste zu klein ist, wird die Benachrichtigungsereignisliste überlaufen. Um diesen Überlauf zu vermeiden, führen Sie einen der folgenden Schritte aus:

   * Verringern Sie das Zeitintervall, das den Thread steuert, der nach neuen Ereignissen abfragt.
   * Vergrößern Sie die Benachrichtigungsliste.

1. Serialisieren Sie die neuesten Benachrichtigungsereigniseinträge im JSON-Format und senden Sie die Einträge zur Nachbearbeitung an einen Remote-Server.

   Der Remote-Server könnte dann die bereitgestellten Daten grafisch in Echtzeit anzeigen.
1. Um den Verlust von Benachrichtigungsereignissen zu erkennen, suchen Sie nach Lücken in der Reihenfolge der Ereignisindexwerte.

   Jedes Benachrichtigungsereignis verfügt über einen Indexwert, der automatisch durch die Variable `NotificationHistory` -Klasse.
