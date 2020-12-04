---
seo-title: Benutzerauthentifizierung
title: Benutzerauthentifizierung
uuid: 191964eb-cd68-47a6-8214-aec01f993df4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Benutzerauthentifizierung{#user-authentication}

Eine Anforderung zum Zugriff auf Adoben kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anforderung ein `AuthenticationToken` enthalten, das von `AuthenticationHandler` generiert wurde. Um auf das Token zuzugreifen und es zu überprüfen, verwenden Sie `RequestMessageBase.getAuthenticationToken()`. Um eine Benutzernamens-/Kennwortanfrage auf dem Client zu starten, verwenden Sie die ActionScript- oder iOS-API.`DRMManager.authenticate()`

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mit der ActionScript 3.0-API fest. `DRMManager.setAuthenticationToken` Verwenden Sie `RequestMessageBase.getRawAuthenticationToken()`, um das benutzerdefinierte Authentifizierungstoken abzurufen. Die Serverimplementierung ist dafür verantwortlich, ob das benutzerdefinierte Authentifizierungstoken gültig ist.
