---
seo-title: Benutzerauthentifizierung
title: Benutzerauthentifizierung
uuid: 5cbd76b9-ff64-4a4b-8cfd-54f05c04eaa3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Benutzerauthentifizierung {#user-authentication}

Eine Adobe Primetime-DRM-Anforderung kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anforderung eine `AuthenticationToken` durch die `AuthenticationHandler`. Wenn Sie auf das Token zugreifen und es überprüfen möchten, müssen Sie es verwenden `RequestMessageBase.getAuthenticationToken()`. Verwenden Sie die `DRMManager.authenticate()` ActionScript- oder iOS-API, um eine Benutzername-/Kennwortanforderung auf dem Client zu starten.

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mithilfe der `DRMManager.setAuthenticationToken` ActionScript 3.0-API fest. Verwenden Sie `RequestMessageBase.getRawAuthenticationToken()` das benutzerdefinierte Authentifizierungstoken. Die Serverimplementierung bestimmt, ob das benutzerdefinierte Authentifizierungstoken gültig ist.
