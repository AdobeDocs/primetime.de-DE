---
title: Über Zertifikate
description: Über Zertifikate
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Über Zertifikate {#about-certificates}

Das Adobe Primetime DRM SDK ist in den folgenden Konfigurationen verfügbar:

* Primetime DRM Production SDK
* Primetime DRM Evaluation SDK
* Primetime DRM-Test-SDK

Um mit dem Primetime DRM SDK einen Lizenzserver zu erstellen, müssen Sie digitale Zertifikate von Adobe abrufen. Digitale Zertifikate (auch einfach als Zertifikate bezeichnet) binden eine Entität wie eine Person, Organisation oder ein System an ein bestimmtes Schlüsselpaar aus öffentlichem und privatem Schlüssel. Digitale Zertifikate können als elektronische Anmeldeinformationen betrachtet werden, die die Identität einer Person, eines Systems oder einer Organisation überprüfen.

Um maximale Flexibilität und erhöhte Sicherheit bei Ihren Bereitstellungsoptionen zu ermöglichen, erfordert das Primetime DRM SDK vier Zertifikate:

* Lizenzserver-Zertifikat

  Das SDK verwendet dieses Zertifikat zum Signieren von Inhaltslizenzen, die für Kunden ausgestellt wurden.
* Packager-Zertifikat

  Das SDK verwendet dieses Zertifikat zum Generieren von DRM-Metadaten beim Verpacken (Verschlüsseln) von Inhalten.
* Transportbescheinigung

  Das SDK verwendet dieses Zertifikat, um die Kommunikation zwischen den Clients und dem Lizenzserver zu sichern.
* Domain-CA-Zertifikat

  Kunden, die einen Domain-Server implementieren möchten, benötigen das Domain CA-Zertifikat. Im Gegensatz zu anderen Zertifikaten wird das Zertifikat der Domain CA nicht von Adobe ausgestellt.

>[!NOTE]
>
>Für das Test-SDK und das Test-SDK werden die Zertifikate License Server, Packager und Transport zu einem einzigen Zertifikat zusammengefasst.
