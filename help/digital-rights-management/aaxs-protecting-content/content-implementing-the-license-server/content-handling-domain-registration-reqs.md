---
seo-title: Bearbeitung von Domänenregistrierungsanfragen
title: Bearbeitung von Domänenregistrierungsanfragen
uuid: e0cef9c4-b2d1-4bec-8dce-50452bc826fb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Bearbeitung von Domänenregistrierungsanfragen{#handling-domain-registration-requests}

Wenn die DRM-Metadaten anzeigen, dass die Domänenregistrierung zum Abspielen des Inhalts erforderlich ist, sollte die Clientanwendung die ActionScript-API DRMManager.addToDeviceGroup() oder die iOS-API joinLicenseDomain() aufrufen. Wenn sich der Client noch nicht beim angegebenen Domänenserver registriert hat (oder wenn die Anwendung eine erneute Anmeldung erzwingt), wird eine Domänenregistrierungsanfrage gesendet. Der Domänenserver bestimmt, ob der Client einer Domäne beitreten darf, und erteilt dem Client eine oder mehrere Domänenberechtigungen.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Domänenservers in Metadaten: + &quot;/flashaccess/domain/v4&quot;. Andernfalls lautet die Anforderungs-URL in den Metadaten &quot;URL des Domänenservers&quot; + &quot;/flashaccess/domain/v3&quot;

Beim Initialisieren der `DomainRegistrationHandler`URL muss die URL des Domänenservers angegeben werden. Diese URL wird in die vom Handler ausgegebenen Domänen-Token aufgenommen, um den Domänenserver anzugeben, der das Token ausgegeben hat. Die URL muss mit der URL des Domänenservers übereinstimmen, die in einer Richtlinie angegeben ist, für die die Domänenregistrierung beim Server erforderlich ist.

Um festzustellen, ob der Client der Domäne beitreten darf, kann der Server die Computer- und Benutzerinformationen in der Anforderung überprüfen. Informationen zum Identifizieren und Zählen von Computern, die zur Domäne gehören, finden Sie unter [Verwenden von](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-using-machine-ids.md) Computerkennungen. Der Server kann auch bestimmen, welcher Domäne der Client beitreten darf. Beachten Sie, dass ein Client nur Mitglied einer Domäne pro URL des Domänenservers sein darf. Wenn auf dem Computer bereits ein Domänentoken für diese Domänenserver-URL vorhanden ist, enthält die Domänenregistrierungsanforderung den aktuellen Domänennamen ( `getRequestDomainName()`). Bei einer Anforderung zum erneuten Verbinden muss der Domänenserver entweder den aktuellen Satz von Domänenberechtigungen für diese Domäne zurückgeben oder einen Fehler zurückgeben (der Domänenserver gibt möglicherweise die Domänenberechtigungen für eine andere Domäne nicht zurück).

Wenn der Domänenserver eine Authentifizierung erfordert, um einer Domäne beizutreten, sollte die Anforderung ein Authentifizierungstoken enthalten. Wie bei einer Lizenzanforderung kann die Domänenregistrierung Benutzername/Kennwort oder benutzerdefinierte Authentifizierung erfordern. Weitere Informationen zum Umgang mit Authentifizierungstoken finden Sie unter [Benutzerauthentifizierung](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-authentication/content-user-authentication.md) .

Der Domänenserver ist für das Speichern und Verwalten der mit der jeweiligen Domäne verknüpften Domänenschlüssel zuständig. Wenn für eine Domäne (die erste Domänenregistrierung) ein neues Schlüsselpaar generiert werden muss, rufen Sie `generateDomainCredential``(String, int, Principal, Date)`auf. Diese Methode generiert ein neues Domänenschlüssel-Paar und ein Domänenzertifikat. Der Domänenserver muss den privaten Schlüssel und das Zertifikat speichern und diese Objekte bereitstellen, wenn nachfolgende Anforderungen für diese Domäne verarbeitet werden. Es ist auch möglich, ein neues Schlüsselpaar für eine Domäne zu generieren, um die Schlüssel zu aktualisieren. Wenn Sie die Schlüssel für eine bestimmte Domäne aktualisieren, müssen Sie `generateDomainCredential` auch die Schlüsselversion inkrementieren.

Jedes Mal, wenn sich ein Computer mit derselben Domäne registriert, sollte derselbe private Domänenschlüssel und dasselbe Zertifikat verwendet werden. Rufen Sie `addDomainCredential(DomainToken, PrivateKey)` auf, eine vorhandene Domänenberechtigung an den Client zurückzugeben. Wenn es mehrere Domänenberechtigungen für die Domäne gibt, weil die Domänenschlüssel geändert wurden, muss der Server Domänenberechtigungen für den aktuellen Domänenschlüssel und alle vorherigen Domänenschlüssel bereitstellen, damit der Client Lizenzen nutzen kann, die an ältere Domänenschlüssel gebunden sind. Dadurch kann eine an ein altes Domänentoken gebundene Lizenz auf einen neu registrierten Computer verschoben und trotzdem abspielbar sein.
