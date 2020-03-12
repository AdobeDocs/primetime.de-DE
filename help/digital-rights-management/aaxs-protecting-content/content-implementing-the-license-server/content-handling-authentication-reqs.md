---
seo-title: Verarbeiten von Authentifizierungsanforderungen
title: Verarbeiten von Authentifizierungsanforderungen
uuid: 036582d4-611c-4772-b247-81a3144fd5d6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verarbeiten von Authentifizierungsanforderungen{#handling-authentication-requests}

Die `AuthenticationHandler` Klasse wird zur Verarbeitung von Authentifizierungsanforderungen verwendet. Es wird nur zur Authentifizierung mit Benutzername und Kennwort verwendet.

Beim Generieren des Authentifizierungstokens muss das Ablaufdatum des Tokens angegeben werden. Benutzerdefinierte Eigenschaften können auch im Token enthalten sein. Falls festgelegt, sind diese Eigenschaften für den Server sichtbar, wenn das Authentifizierungstoken in nachfolgenden Anforderungen gesendet wird. Informationen zum Umgang mit benutzerdefinierten Authentifizierungstoken finden Sie unter [Umgang mit Lizenzanforderungen](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md) .

Der Handler liest eine Authentifizierungsanforderung und analysiert die Anforderungsmeldung, wenn `parseRequest()` sie aufgerufen wird. Die Serverimplementierung prüft die Benutzeranmeldeinformationen in der Anforderung und generiert, wenn die Anmeldeinformationen gültig sind, ein `AuthenticationToken` Objekt durch Aufruf `getRequest().generateAuthToken()`. Wenn `AuthenticationRequestMessage.generateAuthToken()` noch nicht aufgerufen wurde `close()`, wird ein Fehlercode für die Authentifizierung gesendet.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten: + &quot;/flashaccess/authn/v4&quot;. Wenn Protokollversion 3 das Maximum ist, das vom Client oder Server unterstützt wird, senden Adobe Access-Clients Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot;/flashaccess/authn/v3&quot;. Andernfalls werden Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot;/flashaccess/authn/v1&quot; gesendet

