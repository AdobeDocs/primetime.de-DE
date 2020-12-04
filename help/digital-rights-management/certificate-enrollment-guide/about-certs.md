---
seo-title: Grundlagen zu Zertifikaten
title: Grundlagen zu Zertifikaten
uuid: 0b7818b4-bd6a-4f2e-94c2-565e0d735bf8
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Info zu Zertifikaten {#about-certificates}

Das Adobe Primetime DRM SDK ist in den folgenden Konfigurationen verfügbar:

* Primetime DRM Production SDK
* Primetime DRM Evaluation SDK
* Primetime DRM-Testversion-SDK

Um mit dem Primetime-DRM-SDK einen Lizenzserver zu erstellen, müssen Sie digitale Zertifikate von der Adobe abrufen. Digitale Zertifikate (auch einfach als Zertifikate bezeichnet) binden eine Entität wie eine Einzelperson, eine Organisation oder ein System an ein bestimmtes öffentliches und privates Schlüsselpaar. Digitale Zertifikate können als elektronische Anmeldeinformationen betrachtet werden, die die Identität einer Person, eines Systems oder einer Organisation überprüfen.

Um maximale Flexibilität und höhere Sicherheit bei den Bereitstellungsoptionen zu gewährleisten, erfordert das Primetime DRM SDK vier Zertifikate:

* Lizenzserverzertifikat

   Das SDK verwendet dieses Zertifikat zum Signieren von Inhaltslizenzen, die für Clients ausgestellt wurden.
* Packager-Zertifikat

   Das SDK verwendet dieses Zertifikat, um DRM-Metadaten beim Verpacken (Verschlüsseln) von Inhalten zu generieren.
* Transportbescheinigung

   Das SDK verwendet dieses Zertifikat, um die Kommunikation zwischen den Clients und dem Lizenzserver zu sichern.
* Domänenzertifikat

   Kunden, die einen Domänenserver implementieren möchten, benötigen das CA-Domänenzertifikat. Im Gegensatz zu den anderen Zertifikaten wird das CA-Domänenzertifikat nicht von der Adobe ausgestellt.

>[!NOTE]
>
>Für das Test-SDK und das Test-SDK werden die Lizenzserver-, Packager- und Transportzertifikate zu einem einzigen Zertifikat zusammengefasst.

