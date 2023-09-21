---
title: Benutzerauthentifizierung
description: Benutzerauthentifizierung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Benutzerauthentifizierung{#user-authentication}

Eine Adobe Access-Anfrage kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anfrage eine `AuthenticationToken` von der `AuthenticationHandler`. Verwenden Sie zum Zugreifen auf und Überprüfen des Tokens `RequestMessageBase.getAuthenticationToken()`. Verwenden Sie zum Initiieren einer Anfrage zum Benutzernamen/Kennwort auf dem Client die `DRMManager.authenticate()` ActionScript oder iOS-API.

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mithilfe des `DRMManager.setAuthenticationToken` ActionScript 3.0-API. Verwendung `RequestMessageBase.getRawAuthenticationToken()` , um das benutzerdefinierte Authentifizierungstoken abzurufen. Die Serverimplementierung ist für die Bestimmung der Gültigkeit des benutzerdefinierten Authentifizierungstokens verantwortlich.
