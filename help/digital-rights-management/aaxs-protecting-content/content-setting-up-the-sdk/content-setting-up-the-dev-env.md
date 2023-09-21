---
description: Um Adobe® Access™ für die Verwendung einzurichten, kopieren Sie Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Fordern Sie außerdem ein Zertifikat von Adobe Systems Incorporated an. Sie erhalten mehrere Anmeldeinformationen, die zum Schutz der Integrität von verpackten Inhalten, Lizenzen und der Kommunikation zwischen Client und Server verwendet werden.
title: Einrichten der Entwicklungsumgebung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Einrichten des SDK {#setting-up-the-sdk}

Um Adobe® Access™ für die Verwendung einzurichten, kopieren Sie Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Fordern Sie außerdem ein Zertifikat von Adobe Systems Incorporated an. Sie erhalten mehrere Anmeldeinformationen, die zum Schutz der Integrität von verpackten Inhalten, Lizenzen und der Kommunikation zwischen Client und Server verwendet werden.

Das Adobe Access SDK ist in zwei Typen verfügbar:
* ADOBE ACCESS CORE SDK
* ADOBE ACCESS PROFESSIONAL SDK

Die folgende Tabelle zeigt einen grundlegenden Vergleich von Adobe Access SDKs:

| Funktion | ADOBE ACCESS CORE SDK | ADOBE ACCESS PROFESSIONAL SDK |
|---|---|---|
| Funktionen von Flash Access 2.0 | Verfügbar | Verfügbar |
| Schlüsselrotation | - | Verfügbar |
| Domänenunterstützung | Verfügbar | Verfügbar |
| Verbesserte Lizenzketten | Verfügbar | Verfügbar |
| Synchronisierungsmeldungen | Verfügbar | Verfügbar |
| Lizenzvorgenerierung | Verfügbar | Verfügbar |
| Eingebettete Lizenzen | Verfügbar | Verfügbar |

## Einrichten der Entwicklungsumgebung {#setting-up-the-development-environment}

Kopieren Sie von der DVD die folgenden SDK-Dateien zur Verwendung in Ihrer Entwicklungsumgebung und in Ihren Java-Klassenpfad:

* adobe-flashaccess-certs.jar (enthält Adobe-Stammzertifikate)
* adobe-flashaccess-sdk.jar (enthält Adobe Access Core SDK-Klassen)
* adobe-flashaccess-sdk-pro.jar (enthält Adobe Access Professional SDK-Klassen, nur für Professional-Funktionen erforderlich)

Sie benötigen die folgenden JAR-Dateien von Drittanbietern, die sich auch auf der DVD im Ordner &quot;Drittanbieter&quot;des SDK befinden:

* bcmail-jdk15-141.jar
* bcprov-jdk15-141.jar
* commons-discovery-0.4.jar
* commons-logging-1.1.1.jar
* cryptoj.jar
* jaxb-api.jar
* jaxb-impl.jar
* jaxb-libs.jar
* relaxngDatatype.jar
* rm-pdrl.jar
* xsdlib.jar

Zur Leistungsverbesserung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken bereitstellen, die sich im Ordner &quot;third-party/cryptoj&quot;des SDK befinden. Um die native Unterstützung zu aktivieren, fügen Sie die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) zum Pfad hinzu. Die 32-Bit- und 64-Bit-Versionen dieser Bibliotheken werden bereitgestellt. (Beachten Sie, dass die 64-Bit-Version nur verwendet werden sollte, wenn Sie über ein 64-Bit-Betriebssystem verfügen und die 64-Bit-Version von Java ausführen).

Darüber hinaus ist adobe-flashaccess-lcrm.jar ein optionaler Teil des SDK. Diese Datei wird nur für Funktionen benötigt, die mit der Adobe Flash Media Rights Management Server (FMRMS) 1.x-Kompatibilität verbunden sind. Wenn Sie zuvor FMRMS 1.x bereitgestellt haben und Ihre FMRMS-geschützten Inhalte nicht erneut verpacken möchten, müssen Sie Ihrem Lizenzserver Unterstützung hinzufügen, damit er alte Inhalte und Clients verarbeiten kann.
