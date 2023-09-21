---
title: Vorhandene Bereitstellungen aktualisieren
description: Vorhandene Bereitstellungen aktualisieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Vorhandene Bereitstellungen aktualisieren {#upgrading-existing-deployments}

Ersetzen Sie zum Aktualisieren eines Servers, auf dem Version 3.0 Reference Implementation License Server oder Watched Folder Packager ausgeführt wird, die [!DNL .war] -Dateien, die auf Ihrem Anwendungsserver mit den Dateien bereitgestellt werden, die im Adobe Access Reference Implementation Server enthalten sind.

Wenn Sie die Domänenregistrierung mit dem Referenz-Implementierungs-Lizenzserver verwenden möchten, sind mehrere neue Datenbanktabellen erforderlich. Führen Sie zum erneuten Erstellen der gesamten Referenzimplementierungsdatenbank `CreateSampleDB.sql`. Um die vorhandenen Datenbankdatensätze beizubehalten und die neuen Tabellen hinzuzufügen, öffnen Sie `CreateSampleDB.sql`und führen Sie nur die Befehle aus, um die folgenden Tabellen zu erstellen:

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

Die folgenden Eigenschaften müssen zu flashaccess-refimpl.properties hinzugefügt werden, um die Domänenunterstützung zu verwenden:

* `HandlerConfiguration.DomainCAs.n` oder `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` und `DomainRegistrationHandler.ServerCredential.password`oder `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

Die folgenden Eigenschaften müssen hinzugefügt werden [!DNL flashaccess-refimpl.properties] zur Unterstützung der Remote-Schlüsselbereitstellung an iOS-Clients:

* `HandlerConfiguration.KeyServerCertificate` oder `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
