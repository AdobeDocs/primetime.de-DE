---
title: Verarbeiten von Authentifizierungsanforderungen
description: Verarbeiten von Authentifizierungsanforderungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# Verarbeiten von Authentifizierungsanfragen{#handling-authentication-requests}

Die `AuthenticationHandler`-Klasse wird zur Verarbeitung von Authentifizierungsanforderungen verwendet. Es wird nur zur Authentifizierung mit Benutzername und Kennwort verwendet.

Beim Generieren des Authentifizierungstokens muss das Ablaufdatum des Tokens angegeben werden. Benutzerdefinierte Eigenschaften können auch im Token enthalten sein. Falls festgelegt, sind diese Eigenschaften für den Server sichtbar, wenn das Authentifizierungstoken in nachfolgenden Anforderungen gesendet wird. Informationen zum Umgang mit benutzerdefinierten Authentifizierungstoken finden Sie unter [Verarbeiten von Lizenzanforderungen](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md).

Der Handler liest eine Authentifizierungsanforderung und analysiert die Anforderungsmeldung, wenn `parseRequest()` aufgerufen wird. Die Serverimplementierung prüft die Benutzeranmeldeinformationen in der Anforderung. Wenn die Anmeldeinformationen gültig sind, wird ein `AuthenticationToken`-Objekt durch Aufruf von `getRequest().generateAuthToken()` generiert. Wenn `AuthenticationRequestMessage.generateAuthToken()` nicht vor `close()` aufgerufen wird, wird ein Fehlercode für die Authentifizierung gesendet.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten: + &quot;/flashaccess/authn/v4&quot;. Wenn die Protokollversion 3 die vom Client oder Server maximal unterstützte Version ist, senden Adobe Access-Clients Authentifizierungsanforderungen an &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/authn/v3&quot;. Andernfalls werden Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot;/flashaccess/authn/v1&quot; gesendet

