---
seo-title: Benutzerauthentifizierung
title: Benutzerauthentifizierung
uuid: 191964eb-cd68-47a6-8214-aec01f993df4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Benutzerauthentifizierung{#user-authentication}

Eine Adobe Access-Anforderung kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, enthält die Anforderung möglicherweise eine `AuthenticationToken` vom `AuthenticationHandler`. Um auf das Token zuzugreifen und es zu überprüfen, verwenden Sie `RequestMessageBase.getAuthenticationToken()`. Verwenden Sie die `DRMManager.authenticate()` ActionScript- oder iOS-API, um eine Benutzername-/Kennwortanforderung auf dem Client zu starten.

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mithilfe der `DRMManager.setAuthenticationToken` ActionScript 3.0-API fest. Verwenden Sie `RequestMessageBase.getRawAuthenticationToken()` das benutzerdefinierte Authentifizierungstoken. Die Serverimplementierung ist dafür verantwortlich, ob das benutzerdefinierte Authentifizierungstoken gültig ist.
