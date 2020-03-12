---
description: Um Adobe® Access™ für die Verwendung einzurichten, kopieren Sie Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Fordern Sie außerdem ein Zertifikat von Adobe Systems Incorporated an. Sie erhalten mehrere Anmeldeinformationen, die zum Schutz der Integrität von verpackten Inhalten, Lizenzen und der Kommunikation zwischen Client und Server verwendet werden.
seo-description: Um Adobe® Access™ für die Verwendung einzurichten, kopieren Sie Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Fordern Sie außerdem ein Zertifikat von Adobe Systems Incorporated an. Sie erhalten mehrere Anmeldeinformationen, die zum Schutz der Integrität von verpackten Inhalten, Lizenzen und der Kommunikation zwischen Client und Server verwendet werden.
seo-title: Einrichten der Umgebung
title: Einrichten der Umgebung
uuid: 1f192783-9c9a-4342-909a-4881248a85ad
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Einrichten des SDK {#setting-up-the-sdk}

Um Adobe® Access™ für die Verwendung einzurichten, kopieren Sie Dateien von der DVD. Zu diesen Dateien gehören JAR-Dateien mit Code, Zertifikaten und Drittanbieterklassen. Fordern Sie außerdem ein Zertifikat von Adobe Systems Incorporated an. Sie erhalten mehrere Anmeldeinformationen, die zum Schutz der Integrität von verpackten Inhalten, Lizenzen und der Kommunikation zwischen Client und Server verwendet werden.

Das Adobe Access SDK ist in zwei Typen verfügbar:
* Adobe Access Core SDK
* Adobe Access Professional SDK

Die folgende Tabelle zeigt einen grundlegenden Vergleich von Adobe Access-SDKs:

| Funktion | Adobe Access Core SDK | Adobe Access Professional SDK |
|---|---|---|
| Flash Access 2.0-Funktionen | Verfügbar | Verfügbar |
| Schlüsselrotation | - | Verfügbar |
| Domänenunterstützung | Verfügbar | Verfügbar |
| Erweiterte Lizenzketten | Verfügbar | Verfügbar |
| Synchronisierungsmeldungen | Verfügbar | Verfügbar |
| Lizenzvorbereitung | Verfügbar | Verfügbar |
| Eingebettete Lizenzen | Verfügbar | Verfügbar |

## Einrichten der Umgebung {#setting-up-the-development-environment}

Kopieren Sie auf der DVD die folgenden SDK-Dateien zur Verwendung in Ihrer Development-Umgebung und in Ihren Java-Klassenpfad:

* adobe-flashaccess-certs.jar (enthält Adobe-Stammzertifikate)
* adobe-flashaccess-sdk.jar (enthält Adobe Access Core SDK-Klassen)
* adobe-flashaccess-sdk-pro.jar (enthält Adobe Access Professional SDK-Klassen, nur für Professional-Funktionen erforderlich)

Sie benötigen die folgenden JAR-Dateien von Drittanbietern, die sich auch auf der DVD im SDK-Ordner &quot;thirdparty&quot;befinden:

* bcmail-jdk15-141.jar
* bcprov-jdk15-141.jar
* commons-discover-0.4.jar
* commons-logging-1.1.1.jar
* cryptoj.jar
* jaxb-api.jar
* jaxb-impl.jar
* jaxb-libs.jar
* relaxngDatatype.jar
* rm-pdrl.jar
* xsdlib.jar

Zur Verbesserung der Leistung können Sie optional die native Unterstützung für kryptografische Vorgänge aktivieren, indem Sie die plattformspezifischen Bibliotheken bereitstellen, die sich im Ordner &quot;thirdparty/cryptoj&quot;des SDK befinden. Um die native Unterstützung zu aktivieren, fügen Sie dem Pfad die Bibliothek für Ihre Plattform (jsafe.dll für Windows oder libjsafe.so für Linux) hinzu. Die 32-Bit- und 64-Bit-Versionen dieser Bibliotheken stehen zur Verfügung. (Beachten Sie, dass die 64-Bit-Version nur verwendet werden sollte, wenn Sie ein 64-Bit-Betriebssystem haben und die 64-Bit-Version von Java ausgeführt wird).

Außerdem ist adobe-flashaccess-lcrm.jar ein optionaler Teil des SDK. Diese Datei wird nur für Funktionen benötigt, die mit der Kompatibilität mit Adobe Flash Media Rights Management Server (FMRMS) 1.x in Zusammenhang stehen. Wenn Sie zuvor FMRMS 1.x bereitgestellt haben und Ihre FMRMS-geschützten Inhalte nicht erneut verpacken möchten, müssen Sie Ihrem Lizenzserver Unterstützung hinzufügen, damit er alte Inhalte und Clients verarbeiten kann.
