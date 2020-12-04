---
seo-title: Benutzerauthentifizierung
title: Benutzerauthentifizierung
uuid: 5cbd76b9-ff64-4a4b-8cfd-54f05c04eaa3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Benutzerauthentifizierung {#user-authentication}

Eine Adobe Primetime DRM-Anforderung kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anforderung ein `AuthenticationToken` enthalten, das von `AuthenticationHandler` generiert wurde. Wenn Sie auf das Token zugreifen und es überprüfen möchten, müssen Sie `RequestMessageBase.getAuthenticationToken()` verwenden. Um eine Benutzernamens-/Kennwortanfrage auf dem Client zu starten, verwenden Sie die ActionScript- oder iOS-API.`DRMManager.authenticate()`

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mit der ActionScript 3.0-API fest. `DRMManager.setAuthenticationToken` Verwenden Sie `RequestMessageBase.getRawAuthenticationToken()`, um das benutzerdefinierte Authentifizierungstoken abzurufen. Die Serverimplementierung bestimmt, ob das benutzerdefinierte Authentifizierungstoken gültig ist.
