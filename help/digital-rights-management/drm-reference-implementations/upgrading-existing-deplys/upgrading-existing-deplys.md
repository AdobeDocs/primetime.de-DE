---
description: Um einen Server zu aktualisieren, der Version 3.0 Reference Implementation License Server oder Watched Folder Packager unterstützt, müssen Sie die .war-Dateien, die auf einem Anwendungsserver bereitgestellt wurden, durch die Dateien ersetzen, die in Adobe Primetime DRM Reference Implementation Server enthalten sind.
title: Vorhandene Bereitstellungen aktualisieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Übersicht {#upgrade-existing-deployments-overview}

Um einen Server zu aktualisieren, der Version 3.0 Reference Implementation License Server oder Watched Folder Packager unterstützt, müssen Sie die .war-Dateien, die auf einem Anwendungsserver bereitgestellt wurden, durch die Dateien ersetzen, die in Adobe Primetime DRM Reference Implementation Server enthalten sind.

Um die Domänenregistrierung mit dem Referenz-Implementierungslizenzserver zu verwenden, sind mehrere neue Datenbanktabellen erforderlich. Sie müssen die gesamte Referenz-Implementierungsdatenbank neu erstellen und `CreateSampleDB.sql` ausführen.

So bewahren Sie Datenbankdatensätze auf und fügen neue Tabellen hinzu:

1. Öffnen Sie `CreateSampleDB.sql` und führen Sie Befehle aus, die die folgenden Tabellen erstellen:

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. hinzufügen Sie die folgenden Eigenschaften auf [!DNL flashaccess-refimpl.properties], um die Domänenunterstützung zu verwenden:

   * `HandlerConfiguration.DomainCAs.n` oder  `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` und  `DomainRegistrationHandler.ServerCredential.password` oder  `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. hinzufügen Sie die folgenden Eigenschaften zu [!DNL flashaccess-refimpl.properties], um Remote-Key-Versand für iOS-Clients zu unterstützen:

   * `HandlerConfiguration.KeyServerCertificate` oder  `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`