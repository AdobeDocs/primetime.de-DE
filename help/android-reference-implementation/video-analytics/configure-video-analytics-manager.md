---
description: Sie können die Videonutzung in der Primetime-Android-Referenzimplementierung verfolgen, indem Sie sie so konfigurieren, dass sie mit Ihrem Adobe Analytics-Konto funktioniert.
title: Video Analytics konfigurieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Video Analytics konfigurieren {#configure-video-analytics}

Sie können die Videonutzung in der Primetime-Android-Referenzimplementierung verfolgen, indem Sie sie so konfigurieren, dass sie mit Ihrem Adobe Analytics-Konto funktioniert. Die Android-Referenzimplementierung wurde entwickelt, um Videonutzungs- und Heartbeat-Daten an Adobe Analytics zu senden. Um diese Funktion zu aktivieren, müssen Sie sich zunächst an Ihren Adobe Primetime-Support-Mitarbeiter wenden und ein Adobe Analytics-Konto erstellen.

In der Referenzimplementierung müssen Sie zwei Stellen konfigurieren, um die Adobe Analytics-Integration zu aktivieren. Die Videoanalysekonfigurationen zur Laufzeit wirken sich darauf aus, sobald ein neues Video für die Wiedergabe ausgewählt wird (d. h. sobald eine neue PlayerActivities-Aktivität erstellt wurde).

1. Konfigurieren Sie die Ladezeitoptionen in der `ADBMobileConfig.json` Asset-Datei.

   Diese Datei erhalten Sie von Ihrem Adobe-Support-Mitarbeiter. Sie ist standardmäßig nicht im Primetime SDK-Bundle enthalten. Weitere Informationen zu den Einstellungen in dieser Konfigurationsdatei finden Sie im Android-Programmierhandbuch hier: Videoanalyse initialisieren und konfigurieren .
1. Konfigurieren von Laufzeitoptionen im Menü &quot;Einstellungen für Referenzimplementierung&quot;

   ![](assets/img_psdk_ref_impl_va-settings-menu.png)

   | Laufzeitoptionen | Beschreibung |
   |---|---|
   | Video Analytics-Tracking-Server | URL des Back-End-Erfassungsendpunkts der Videoanalyse. Hier werden alle Video Heartbeat-Tracking-Aufrufe gesendet. |
   | Auftrags-ID | Die Kennung des Verarbeitungsauftrags. Dies gibt dem Backend-Endpunkt an, welche Art von Verarbeitung für die Video-Tracking-Aufrufe angewendet werden soll. |
   | Kanal | Der Name des Kanals, in dem der Benutzer den Inhalt anschaut. Bei einer Mobile App ist dies normalerweise der Name der App. |
   | Herausgeber | Der Name des Herausgebers des Inhalts |
   | Debug-Protokollierung | Aktiviert eine umfangreiche Protokollierung. Standardmäßig deaktiviert, kann dies die Leistung beeinträchtigen, wenn sie aktiviert ist. Deaktivieren Sie dies daher für eine Produktionsumgebung. |
   | Ruhezustand | Wenn diese Option aktiviert ist, werden keine Netzwerkaufrufe durchgeführt. Dies wäre also für das lokale Debugging nützlich, muss aber für eine Produktionsumgebung deaktiviert werden. |
