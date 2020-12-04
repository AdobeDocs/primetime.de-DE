---
description: Sie können die Videonutzung in der Primetime-Android-Referenzimplementierung verfolgen, indem Sie sie für die Verwendung mit Ihrem Adobe Analytics-Konto konfigurieren.
seo-description: Sie können die Videonutzung in der Primetime-Android-Referenzimplementierung verfolgen, indem Sie sie für die Verwendung mit Ihrem Adobe Analytics-Konto konfigurieren.
seo-title: Videoanalyse konfigurieren
title: Videoanalyse konfigurieren
uuid: ce2ebab3-b3c8-472a-9c54-16ddb1c3cc4e
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '330'
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