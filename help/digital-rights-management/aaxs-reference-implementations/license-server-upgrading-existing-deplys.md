---
seo-title: Vorhandene Bereitstellungen aktualisieren
title: Vorhandene Bereitstellungen aktualisieren
uuid: 57e62a88-e541-435c-8274-7f1602548601
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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

