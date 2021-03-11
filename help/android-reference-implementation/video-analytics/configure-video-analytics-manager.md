---
description: Sie können die Videonutzung in der Primetime-Android-Referenzimplementierung verfolgen, indem Sie sie für die Verwendung mit Ihrem Adobe Analytics-Konto konfigurieren.
title: Videoanalyse konfigurieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Videoanalyse konfigurieren {#configure-video-analytics}

Sie können die Videonutzung in der Primetime-Android-Referenzimplementierung verfolgen, indem Sie sie für die Verwendung mit Ihrem Adobe Analytics-Konto konfigurieren. Die Android-Referenzimplementierung wurde entwickelt, um Videonutzungs- und Heartbeat-Daten an Adobe Analytics zu senden. Um diese Funktion zu aktivieren, müssen Sie sich zuerst an Ihren Adobe Primetime-Kundenbetreuer wenden und ein Adobe Analytics-Konto erstellen.

In der Referenzimplementierung müssen Sie zwei Stellen konfigurieren, um die Adobe Analytics-Integration zu aktivieren. Die Laufzeitkonfigurationen von Video Analytics wirken sich darauf aus, sobald ein neues Video zur Wiedergabe ausgewählt wurde (d. h. nachdem eine neue PlayerAction erstellt wurde).

1. Konfigurieren Sie die Optionen für die Ladezeit in der Asset-Datei `ADBMobileConfig.json`.

   Diese Datei wird von Ihrem Kundenbetreuer zur Adobe bereitgestellt. Sie ist nicht standardmäßig im Primetime SDK-Bundle enthalten. Weitere Informationen zu den Einstellungen in dieser Konfigurationsdatei finden Sie im Android-Programmierhandbuch hier: Initialisieren und Konfigurieren der Videoanalyse.
1. Konfigurieren von Laufzeitoptionen im Menü &quot;Einstellungen für die Referenzimplementierung&quot;

   ![](assets/img_psdk_ref_impl_va-settings-menu.png)

   | Laufzeitoptionen | Beschreibung |
   |---|---|
   | Video Analytics-Tracking-Server | URL des Back-End-Erfassungsendpunkts der Videoanalyse. Hier werden alle Video Heartbeat-Verfolgungsaufrufe gesendet. |
   | Job-ID | Die ID des Verarbeitungsauftrags. Dies zeigt dem Back-End-Endpunkt an, welche Art von Verarbeitung für die Videoverfolgungsaufrufe angewendet werden soll. |
   | Kanal | Der Name des Kanals, auf dem der Benutzer den Inhalt ansieht. Bei einer mobilen Anwendung ist dies normalerweise der Name der Anwendung. |
   | Herausgeber | Der Name des Herausgebers des Inhalts |
   | Debug-Protokollierung | Aktiviert umfangreiche Protokollierung. Standardmäßig deaktiviert, kann dies die Leistung beeinträchtigen, wenn sie aktiviert ist. Sie können dies daher für eine Produktions-Umgebung deaktivieren. |
   | Ruhe | Wenn dies aktiviert ist, werden keine Netzwerkaufrufe durchgeführt. Dies wäre für das lokale Debugging nützlich, muss aber für eine Produktions-Umgebung deaktiviert werden. |