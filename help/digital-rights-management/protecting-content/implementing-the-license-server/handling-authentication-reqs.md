---
title: Verarbeiten von Authentifizierungsanforderungen
description: Verarbeiten von Authentifizierungsanforderungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Verarbeiten von Authentifizierungsanforderungen {#handle-authentication-requests}

Die `AuthenticationHandler`-Klasse wird zur Verarbeitung von Authentifizierungsanforderungen verwendet. Es wird nur zur Authentifizierung mit Benutzername und Kennwort verwendet.

Beim Generieren des Authentifizierungstokens muss das Ablaufdatum des Tokens angegeben werden. Benutzerdefinierte Eigenschaften können auch im Token enthalten sein. Falls festgelegt, sind diese Eigenschaften für den Server sichtbar, wenn das Authentifizierungstoken in nachfolgenden Anforderungen gesendet wird. Informationen zum Umgang mit benutzerdefinierten Authentifizierungstoken finden Sie unter [Verarbeiten von Lizenzanforderungen](../../protecting-content/implementing-the-license-server/handling-license-reqs/license-handling-classes.md).

Der Handler liest eine Authentifizierungsanforderung und analysiert die Anforderungsmeldung, wenn `parseRequest()` aufgerufen wird. Die Serverimplementierung prüft die Benutzeranmeldeinformationen in der Anforderung. Wenn die Anmeldeinformationen gültig sind, wird ein `AuthenticationToken`-Objekt durch Aufruf von `getRequest().generateAuthToken()` generiert. Wenn `AuthenticationRequestMessage.generateAuthToken()` nicht vor `close()` aufgerufen wird, wird ein Fehlercode für die Authentifizierung gesendet.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten: + &quot; [!DNL /flashaccess/authn/v4]&quot;. Wenn Protokollversion 3 das Maximum ist, das vom Client oder Server unterstützt wird, stellen Adobe Primetime DRM-Clients dann Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot; [!DNL /flashaccess/authn/v3]&quot;ein. Andernfalls werden Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot; [!DNL /flashaccess/authn/v1]&quot; gesendet

