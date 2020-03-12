---
seo-title: Domänenregistrierungsanfragen bearbeiten
title: Domänenregistrierungsanfragen bearbeiten
uuid: d92db6c2-5a16-41ea-a1aa-541c59780678
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Domänenregistrierungsanfragen bearbeiten {#handle-domain-registration-requests}

Wenn die DRM-Metadaten anzeigen, dass die Domänenregistrierung zum Abspielen des Inhalts erforderlich ist, sollte die Clientanwendung die `DRMManager.addToDeviceGroup()` ActionScript-API oder die `joinLicenseDomain()` iOS-API aufrufen. Wenn sich der Client noch nicht beim angegebenen Domänenserver registriert hat (oder wenn die Anwendung eine erneute Anmeldung erzwingt), wird eine Domänenregistrierungsanfrage gesendet. Der Domänenserver bestimmt, ob der Client einer Domäne beitreten darf, und erteilt dem Client eine oder mehrere Domänenberechtigungen.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Domänenservers in Metadaten: + &quot; [!DNL /flashaccess/domain/v4]&quot;. Andernfalls lautet die Anforderungs-URL in den Metadaten &quot; + [!DNL /flashaccess/domain/v3]&quot;

Beim Initialisieren der URL `DomainRegistrationHandler`müssen Sie die URL des Domänenservers angeben. Diese URL wird dann in die Domänentokens aufgenommen, die vom Handler ausgegeben werden, um dem Domänenserver anzuzeigen, dass das Token ausgegeben wurde. Die URL muss mit der URL des Domänenservers übereinstimmen, die in jeder DRM-Richtlinie angegeben ist, für die die Domänenregistrierung beim Server erforderlich ist.

Um festzustellen, ob der Client der Domäne beitreten darf, kann der Server die Computer- und Benutzerinformationen in der Anforderung überprüfen. Der Server kann auch bestimmen, welcher Domäne der Client beitreten darf.

>[!NOTE]
>
>Ein Client kann nur Mitglied einer Domäne pro URL des Domänenservers sein. Wenn auf dem Computer bereits ein Domänentoken für diese Domänenserver-URL vorhanden ist, enthält die Domänenregistrierungsanforderung den aktuellen Domänennamen ( `getRequestDomainName()`).

Bei einer Anforderung zum erneuten Verbinden muss der Domänenserver entweder den aktuellen Satz von Domänenberechtigungen für diese Domäne zurückgeben oder einen Fehler zurückgeben. Der Domänenserver gibt die Domänenberechtigungen für eine andere Domäne möglicherweise nicht zurück.

Informationen zum Identifizieren und Zählen von Computern, die zur Domäne gehören, finden Sie unter [Verwenden von](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#use-machine-identifiers) Computerkennungen.

Wenn der Domänenserver eine Authentifizierung erfordert, um einer Domäne beizutreten, sollte die Anforderung ein Authentifizierungstoken enthalten. Wie bei einer Lizenzanforderung kann die Domänenregistrierung Benutzername/Kennwort oder benutzerdefinierte Authentifizierung erfordern.

Weitere Informationen zum Verwalten von Authentifizierungstoken finden Sie unter [Benutzerauthentifizierung](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#user-authentication) .

Der Domänenserver ist für das Speichern und Verwalten der Domänenschlüssel verantwortlich, die mit jeder Domäne verknüpft sind. Wenn für eine Domäne (die erste Domänenregistrierung) ein neues Schlüsselpaar generiert werden muss, müssen Sie dieses aufrufen `generateDomainCredential(String, int, Principal, Date)`. Diese Methode generiert ein neues Domänenschlüssel-Paar und ein Domänenzertifikat. Der Domänenserver muss den privaten Schlüssel und das Zertifikat speichern und diese Objekte bereitstellen, wenn nachfolgende Anforderungen für diese Domäne verarbeitet werden. Es ist auch möglich, ein neues Schlüsselpaar für eine Domäne zu generieren, um die Schlüssel zu aktualisieren. Wenn Sie die Schlüssel für eine bestimmte Domäne aktualisieren, stellen Sie sicher, dass Sie die Schlüsselversion in inkrementieren `generateDomainCredential`.

Jedes Mal, wenn sich ein Computer mit derselben Domäne registriert, sollte derselbe private Schlüssel und dasselbe Zertifikat für die Domäne verwendet werden. Rufen Sie `addDomainCredential(DomainToken, PrivateKey)` auf, eine vorhandene Domänenberechtigung an den Client zurückzugeben. Wenn es mehrere Domänenberechtigungen für die Domäne gibt, weil die Domänenschlüssel geändert wurden, muss der Server Domänenberechtigungen für den aktuellen Domänenschlüssel und alle vorherigen Domänenschlüssel bereitstellen, damit der Client Lizenzen nutzen kann, die an ältere Domänenschlüssel gebunden sind. Dadurch kann eine an ein altes Domänentoken gebundene Lizenz auf einen neu registrierten Computer verschoben und trotzdem abspielbar sein.
