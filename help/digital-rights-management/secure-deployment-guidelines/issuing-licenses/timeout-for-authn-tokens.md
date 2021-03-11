---
description: Alle Authentifizierungstoken, die vom Adobe Primetime DRM SDK generiert werden, haben ein Zeitüberschreitungsintervall, um die Anwendungssicherheit zu schützen.
title: Timeout für Authentifizierungstoken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Timeout für Authentifizierungstoken{#timeout-for-authentication-tokens}

Alle Authentifizierungstoken, die vom Adobe Primetime DRM SDK generiert werden, haben ein Zeitüberschreitungsintervall, um die Anwendungssicherheit zu schützen.

Der Ablauf für das Authentifizierungstoken wird bei der Bearbeitung einer Authentifizierungsanforderung mit dem Primetime DRM SDK angegeben. Nach Ablauf ist das Token nicht mehr gültig und der Benutzer muss sich erneut beim Lizenzserver authentifizieren.

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).
