---
description: Um einen Server zu aktualisieren, der Version 3.0 Reference Implementation License Server oder Watched Folder Packager unterstützt, müssen Sie die .war-Dateien, die auf einem Anwendungsserver bereitgestellt wurden, durch die Dateien ersetzen, die in Adobe Primetime DRM Reference Implementation Server enthalten sind.
seo-description: Um einen Server zu aktualisieren, der Version 3.0 Reference Implementation License Server oder Watched Folder Packager unterstützt, müssen Sie die .war-Dateien, die auf einem Anwendungsserver bereitgestellt wurden, durch die Dateien ersetzen, die in Adobe Primetime DRM Reference Implementation Server enthalten sind.
seo-title: Vorhandene Bereitstellungen aktualisieren
title: Vorhandene Bereitstellungen aktualisieren
uuid: 1a40aae9-f639-41fa-b42d-cf8cdfcde694
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Übersicht {#upgrade-existing-deployments-overview}

Um einen Server zu aktualisieren, der Version 3.0 Reference Implementation License Server oder Watched Folder Packager unterstützt, müssen Sie die .war-Dateien, die auf einem Anwendungsserver bereitgestellt wurden, durch die Dateien ersetzen, die in Adobe Primetime DRM Reference Implementation Server enthalten sind.

Um die Domänenregistrierung mit dem Referenz-Implementierungslizenzserver zu verwenden, sind mehrere neue Datenbanktabellen erforderlich. Sie müssen die gesamte Referenz-Implementierungsdatenbank neu erstellen und ausführen `CreateSampleDB.sql`.

So bewahren Sie Datenbankdatensätze auf und fügen neue Tabellen hinzu:

1. Öffnen `CreateSampleDB.sql` und führen Sie Befehle aus, die die folgenden Tabellen erstellen:

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. Hinzufügen Sie die folgenden Eigenschaften, um die Domänenunterstützung zu verwenden: [!DNL flashaccess-refimpl.properties]

   * `HandlerConfiguration.DomainCAs.n` os `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` und `DomainRegistrationHandler.ServerCredential.password``RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. Hinzufügen Sie die folgenden Eigenschaften, [!DNL flashaccess-refimpl.properties] um Remote-Key-Versand für iOS-Clients zu unterstützen:

   * `HandlerConfiguration.KeyServerCertificate` oder `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`