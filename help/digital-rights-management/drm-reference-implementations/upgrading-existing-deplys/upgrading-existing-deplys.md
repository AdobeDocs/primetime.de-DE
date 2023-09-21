---
description: Um einen Server zu aktualisieren, der Version 3.0 Reference Implementation License Server oder Watched Folder Packager unterstützt, müssen Sie die auf einem Anwendungsserver bereitgestellten .war-Dateien durch die Dateien ersetzen, die im Adobe Primetime DRM Reference Implementation Server enthalten sind.
title: Vorhandene Bereitstellungen aktualisieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Übersicht {#upgrade-existing-deployments-overview}

Um einen Server zu aktualisieren, der Version 3.0 Reference Implementation License Server oder Watched Folder Packager unterstützt, müssen Sie die auf einem Anwendungsserver bereitgestellten .war-Dateien durch die Dateien ersetzen, die im Adobe Primetime DRM Reference Implementation Server enthalten sind.

Um die Domänenregistrierung mit dem Referenz-Implementierungs-Lizenzserver zu verwenden, sind mehrere neue Datenbanktabellen erforderlich. Sie müssen die gesamte Referenzimplementierungsdatenbank neu erstellen und ausführen `CreateSampleDB.sql`.

So bewahren Sie Datenbankdatensätze auf und fügen neue Tabellen hinzu:

1. Öffnen `CreateSampleDB.sql` und führen Befehle aus, die die folgenden Tabellen erstellen:

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. Fügen Sie die folgenden Eigenschaften zu [!DNL flashaccess-refimpl.properties] zur Verwendung der Domain-Unterstützung:

   * `HandlerConfiguration.DomainCAs.n` oder `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` und `DomainRegistrationHandler.ServerCredential.password` oder `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. Fügen Sie die folgenden Eigenschaften zu [!DNL flashaccess-refimpl.properties] zur Unterstützung der Remote-Schlüsselbereitstellung an iOS-Clients:

   * `HandlerConfiguration.KeyServerCertificate` oder `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
