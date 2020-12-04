---
title: Einrichten von Adobe Primetime Ad Insertion
description: Einrichten von Adobe Primetime Ad Insertion
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# Einrichten von Adobe Primetime Ad Insertion {#ptai-setup}

Die Einrichtung von Primetime Ad Insertion erfolgt wie folgt:

1. Integrieren Sie Ihren Ad-Server in Primetime-Ad Insertion, indem Sie sich bei der Primetime-Ad Insertion-Konsole anmelden und Umleitungsregeln einrichten. Weitere Informationen finden Sie unter [Integration Ihres Anzeigenservers](integrate-ad-server.md).

1. Konfigurieren Sie Kanal oder Plattformen in der Primetime-Ad Insertion, um angemessene Berichte-Abmessungen sicherzustellen.

1. Konfigurieren und integrieren Sie Ihr CDN in Primetime Ad Insertion. Weitere Informationen finden Sie unter [Integration Ihres CDN](integrate-cdn.md).

1. Stellen Sie fest, ob für Ihren Anzeigenarbeitsablauf eine Just-in-time-Anzeigenumverpackung erforderlich ist. Wenden Sie sich an Ihren Primetime-Support-Mitarbeiter, um den Dienst zu aktivieren.

1. Aktualisieren Sie Ihre Anwendung, um die [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) zum Erstellen und Empfangen von Anforderungen für Primetime-Ad Insertion zu verwenden, und konfigurieren Sie Ihre Anwendung für die Unterstützung. Weitere Informationen finden Sie unter [Anzeigenverfolgung](set-up-ad-tracking.md).

1. Testen Sie Ihre Anwendung, um eine korrekte Anzeige sicherzustellen. <!-- using the [Debugging tools](troubleshoot-and-debug.md).-->

1. Testen Sie Ihre Anwendungen, um sicherzustellen, dass die Anzeigenverfolgung und Impressions-Beacons ordnungsgemäß ausgelöst werden.<!-- using the [Reporting](reporting-and-billing.md).-->
