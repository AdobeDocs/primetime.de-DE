---
title: Vorhandene Bereitstellungen aktualisieren
description: Vorhandene Bereitstellungen aktualisieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Vorhandene Bereitstellungen aktualisieren {#upgrading-existing-deployments}

Ersetzen Sie zum Aktualisieren eines Servers, auf dem die Version 3.0 Reference Implementation License Server oder der Watched Folder Packager ausgeführt wird, die auf Ihrem Anwendungsserver bereitgestellten [!DNL .war]-Dateien durch die Dateien, die im Adobe Access Reference Implementation Server enthalten sind.

Wenn Sie die Domänenregistrierung mit dem Referenz-Implementierungslizenzserver verwenden möchten, sind mehrere neue Datenbanktabellen erforderlich. Um die gesamte Referenz-Implementierungsdatenbank neu zu erstellen, führen Sie `CreateSampleDB.sql` aus. Um die vorhandenen Datenbankdatensätze beizubehalten und die neuen Tabellen hinzuzufügen, öffnen Sie `CreateSampleDB.sql`und führen Sie nur die Befehle aus, um die folgenden Tabellen zu erstellen:

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

Die folgenden Eigenschaften müssen zu flashaccess-refimpl.properties hinzugefügt werden, um die Domänenunterstützung zu verwenden:

* `HandlerConfiguration.DomainCAs.n` oder  `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` und  `DomainRegistrationHandler.ServerCredential.password`oder  `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

Die folgenden Eigenschaften müssen zu [!DNL flashaccess-refimpl.properties] hinzugefügt werden, um Remote-Key-Versand für iOS-Clients zu unterstützen:

* `HandlerConfiguration.KeyServerCertificate` oder  `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`

