---
title: Umgang mit Domänenregistrierungsanfragen
description: Umgang mit Domänenregistrierungsanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Umgang mit Domänenregistrierungsanfragen{#handling-domain-registration-requests}

Wenn die DRM-Metadaten darauf hinweisen, dass die Domänenregistrierung zum Abspielen des Inhalts erforderlich ist, sollte die Client-Anwendung die ActionScript-API DRMManager.addToDeviceGroup() oder die iOS-API joinLicenseDomain() aufrufen. Wenn sich der Client noch nicht beim angegebenen Domain-Server registriert hat (oder wenn die Anwendung eine erneute Verknüpfung erzwingt), wird eine Domänenregistrierungsanfrage gesendet. Der Domänenserver bestimmt, ob der Client einer Domäne beitreten darf, und erteilt dem Client eine oder mehrere Domänenberechtigungen.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Wenn sowohl der Client als auch der Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;Domain Server URL in metadata: + &quot;/flashaccess/domain/v4&quot;. Andernfalls lautet die Anforderungs-URL Domain Server URL in den Metadaten &quot;+ &quot;/flashaccess/domain/v3&quot;

Bei der Initialisierung der `DomainRegistrationHandler`angegeben ist, muss die URL des Domänenservers angegeben werden. Diese URL ist in den Domänen-Token enthalten, die vom Handler ausgestellt wurden, um den Domänenserver anzugeben, der das Token ausgegeben hat. Die URL muss mit der URL des Domänenservers übereinstimmen, die in einer Richtlinie angegeben ist, für die eine Domänenregistrierung beim Server erforderlich ist.

Um festzustellen, ob der Client berechtigt ist, der Domäne beizutreten, kann der Server den Computer und die Benutzerinformationen in der Anfrage überprüfen. Siehe [Verwenden von Maschinenkennungen](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-using-machine-ids.md) für Informationen zur Identifizierung und Zählung von Computern, die zur Domäne gehören. Der Server kann auch bestimmen, welcher Domain der Client beitreten darf. Beachten Sie, dass ein Client nur Mitglied einer Domäne pro Domain-Server-URL sein darf. Wenn der Computer bereits über ein Domänen-Token für diese Domänen-Server-URL verfügt, enthält die Domänenregistrierungsanforderung den aktuellen Domänennamen ( `getRequestDomainName()`). Bei einer erneuten Join-Anfrage muss der Domänenserver entweder den aktuellen Satz von Domänenanmeldeinformationen für diese Domäne zurückgeben oder einen Fehler zurückgeben (der Domänenserver gibt möglicherweise nicht die Domänenberechtigungen für eine andere Domäne zurück).

Wenn der Domänenserver eine Authentifizierung erfordert, um einer Domäne beizutreten, sollte die Anfrage ein Authentifizierungstoken enthalten. Wie bei einer Lizenzanfrage kann die Domänenregistrierung einen Benutzernamen/ein Kennwort oder eine benutzerdefinierte Authentifizierung erfordern. Siehe [Benutzerauthentifizierung](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-authentication/content-user-authentication.md) für Details zur Handhabung von Authentifizierungstoken.

Der Domain-Server ist für die Speicherung und Verwaltung der Domain-Schlüssel für die einzelnen Domänen verantwortlich. Wenn für eine Domäne (die erste Domänenregistrierung für die Domäne) ein neues Schlüsselpaar generiert werden muss, rufen Sie auf `generateDomainCredential` `(String, int, Principal, Date)`. Diese Methode generiert ein neues Domänenschlüsselpaar und ein neues Domänenzertifikat. Der Domänenserver muss den privaten Schlüssel und das Zertifikat speichern und diese Objekte bereitstellen, wenn nachfolgende Anforderungen für diese Domäne verarbeitet werden. Es ist auch möglich, ein neues Schlüsselpaar für eine Domäne zu generieren, um die Schlüssel zu aktualisieren. Wenn Sie die Schlüssel für eine bestimmte Domäne aktualisieren, müssen Sie die Schlüsselversion in `generateDomainCredential` sowie.

Jedes Mal, wenn sich ein Computer bei derselben Domäne registriert, sollten derselbe private Schlüssel und dasselbe Zertifikat der Domäne verwendet werden. Aufrufen `addDomainCredential(DomainToken, PrivateKey)` , um dem Client eine vorhandene Domänenberechtigung zurückzugeben. Wenn mehrere Domänenberechtigungen für die Domäne vorhanden sind, weil die Domänenschlüssel geändert wurden, muss der Server Domänenberechtigungen für den aktuellen Domänenschlüssel und alle vorherigen Domänenschlüssel angeben, damit der Client Lizenzen nutzen kann, die an ältere Domänenschlüssel gebunden sind. Dadurch kann eine an ein altes Domain-Token gebundene Lizenz auf einen neu registrierten Computer verschoben und trotzdem wiedergegeben werden.
