---
title: Erste Schritte
description: Erste Schritte
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Erste Schritte {#getting-started}

In diesem Dokument werden die Schritte für eine schnelle Einrichtung und Bereitstellung eines Adobe Primetime DRM-Ökosystems beschrieben, das mithilfe des progressiven Downloads Inhalte verteilt, sowie des Primetime DRM-Servers für geschütztes Streaming für die Lizenzverteilung. Weitere Informationen zu jedem Schritt finden Sie in den folgenden Handbüchern:

* *Verwenden des Primetime-DRM-Servers zum Schutz von Inhalten*
* *Verwenden des Primetime-DRM-Servers für geschütztes Streaming*

Der Primetime-DRM-Server für geschütztes Streaming ist ein Server mit minimalen Funktionen, der keinen Quellcode enthält. Einen anpassbaren Server mit vollständiger Java-Quelle finden Sie im Abschnitt *Verwenden der Primetime-DRM-Referenzimplementierungen* Handbuch. Wenn Sie einen Referenz-Lizenzserver einrichten, ersetzt dieser die *Primetime DRM Server für geschütztes Streaming einrichten und bereitstellen (Lizenzserver)* Schritt.

## Voraussetzungen {#prerequisites}

Führen Sie die folgenden Aufgaben aus, bevor Sie beginnen:

* Holen Sie sich zwei Windows- oder Linux-Computer:

   * Ein Computer wird der Lizenzserver sein.
   * Ein Computer ist der Inhaltsserver.

* Installieren Sie die folgenden Anwendungen auf beiden Computern:

   * Tomcat 6.0.18
   * Java 1.6

## Zertifikate abrufen {#obtain-certificates}

Nachdem die SDK-Software bereitgestellt wurde, erhält der vorgesehene Unternehmenszertifikatadministrator eine Einladung zum Abschließen des Registrierungsprozesses für Adobe Primetime DRM-Zertifikatregistrierungen. Weitere Informationen finden Sie unter *Handbuch zur Primetime-DRM-Zertifikatregistrierung*.

1. Der Administrator benennt mindestens eine Person, die als Zertifikatanforderer fungiert.
1. Der Zertifikatanforderer generiert einen privaten Schlüssel und eine CSR.
1. Der Antragsteller sendet eine Zertifikatanforderung.
1. Der Unternehmensadministrator genehmigt die Anfrage.
1. Der Adobe-Zertifikatadministrator bestätigt die Übermittlung.
1. Der Anforderer erhält das Zertifikat, bindet das Zertifikat mit dem privaten Schlüssel und stellt das Zertifikat bereit. wie in beschrieben.

   Weitere Informationen zur Bereitstellung des Zertifikats finden Sie unter *Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming* Handbuch.
1. Die Schritte 3 bis 6 müssen für jeden Zertifikatstyp ausgeführt werden.

   Für die Primetime DRM Production-Version muss der Antragsteller separate Anfragen für die Lizenzserver-, Verpackungs- und Transportzertifikate stellen, die für zwei Jahre gültig sind.

   Kunden, die die Primetime DRM Evaluation oder Testversionen verwenden, benötigen nur ein Zertifikat, das für 1 Jahr/90 Tage gültig ist.
