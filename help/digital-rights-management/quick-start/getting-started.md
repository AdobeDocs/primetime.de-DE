---
seo-title: Erste Schritte
title: Erste Schritte
uuid: 2002cf94-c8a7-4820-a560-6d9f7f33ee97
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# Erste Schritte {#getting-started}

In diesem Dokument werden die Schritte für eine schnelle Einrichtung und Bereitstellung eines Adobe Primetime DRM-Ökosystems beschrieben, das zum Verteilen von Inhalten progressives Herunterladen verwendet, und der Primetime DRM-Server für Protected Streaming für die Lizenzverteilung. Weitere Details zu jedem Schritt finden Sie in den folgenden Handbüchern:

* *Verwenden des Primetime DRM-Servers zum Schutz von Inhalten*
* *Verwenden des Primetime-DRM-Servers für das geschützte Streaming*

Der Primetime-DRM-Server für geschütztes Streaming ist ein Server mit minimaler Funktionalität, der keinen Quellcode enthält. Einen modifizierbaren Server mit vollständiger Java-Quelle finden Sie im Handbuch *Verwenden der Primetime-DRM-Referenzimplementierungen*. Wenn Sie einen Referenzlizenzserver einrichten, ersetzt dieser den Schritt *Setup und Bereitstellung des Primetime DRM-Servers für geschütztes Streaming (Lizenzserver)*.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, führen Sie die folgenden Aufgaben durch:

* Zwei Windows- oder Linux-Computer:

   * Ein Computer wird der Lizenzserver sein.
   * Ein Computer ist der Content Server.

* Installieren Sie die folgenden Anwendungen auf beiden Computern:

   * Tomcat 6.0.18
   * Java 1.6

## Zertifikate abrufen {#obtain-certificates}

Nachdem die SDK-Software bereitgestellt wurde, erhält der angegebene Zertifikatadministrator eine Einladung zum Abschluss des Registrierungsvorgangs für das Adobe Primetime DRM-Zertifikat. Weitere Informationen finden Sie im Handbuch *Primetime DRM-Zertifikatregistrierungsanleitung*.

1. Der Administrator benennt mindestens eine Person, die als Zertifikatanforderer fungiert.
1. Der Zertifikatanforderer generiert einen privaten Schlüssel und eine CSR.
1. Der Anforderer sendet eine Zertifikatanforderung.
1. Der Administrator der Firma genehmigt die Anforderung.
1. Der Zertifikatadministrator der Adobe bestätigt die Übermittlung.
1. Der Anforderer empfängt das Zertifikat, bindet das Zertifikat mit dem privaten Schlüssel und stellt das Zertifikat bereit. wie in beschrieben.

   Weitere Informationen zur Bereitstellung des Zertifikats finden Sie im Handbuch *Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming*.
1. Die Schritte 3 bis 6 müssen für jeden Zertifikatstyp ausgefüllt werden.

   Für die Primetime-DRM-Produktionsversion muss der Anforderer separate Anforderungen für Lizenzserver-, Verpackungs- und Transportzertifikate stellen, die zwei Jahre gültig sind.

   Kunden, die die Primetime DRM Evaluation- oder Testversion verwenden, benötigen nur ein Zertifikat, das für 1 Jahr/90 Tage gültig ist.