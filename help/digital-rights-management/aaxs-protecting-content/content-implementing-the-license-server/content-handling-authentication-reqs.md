---
title: Umgang mit Authentifizierungsanfragen
description: Umgang mit Authentifizierungsanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Umgang mit Authentifizierungsanfragen{#handling-authentication-requests}

Die `AuthenticationHandler` -Klasse wird zur Verarbeitung von Authentifizierungsanforderungen verwendet. Sie wird nur für die Authentifizierung mit Benutzername/Kennwort verwendet.

Beim Generieren des Authentifizierungstokens muss das Ablaufdatum des Tokens angegeben werden. Benutzerdefinierte Eigenschaften können auch im Token enthalten sein. Wenn diese Eigenschaften festgelegt sind, sind sie für den Server sichtbar, wenn das Authentifizierungstoken in nachfolgenden Anfragen gesendet wird. Siehe [Handhabung von Lizenzanfragen](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md) für Informationen zum Umgang mit benutzerdefinierten Authentifizierungstoken.

Der Handler liest eine Authentifizierungsanforderung und analysiert die Anforderungsmeldung, wenn `parseRequest()` aufgerufen wird. Die Serverimplementierung überprüft die Benutzeranmeldeinformationen in der Anfrage. Wenn die Anmeldeinformationen gültig sind, generiert eine `AuthenticationToken` Objekt durch Aufruf von `getRequest().generateAuthToken()`. Wenn `AuthenticationRequestMessage.generateAuthToken()` wird nicht vor aufgerufen `close()`, wird ein Fehlercode für Authentifizierungsfehler gesendet.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Wenn sowohl der Client als auch der Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;Lizenzserver-URL in Metadaten: + &quot;/flashaccess/authn/v4&quot;. Wenn die Protokollversion 3 das Maximum ist, das entweder vom Client oder vom Server unterstützt wird, senden Adobe Access-Clients Authentifizierungsanforderungen an &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/authn/v3&quot;. Andernfalls werden Authentifizierungsanfragen an &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/authn/v1&quot;gesendet
