---
description: Alle Authentifizierungstoken, die vom Adobe Primetime DRM SDK generiert werden, haben ein Zeitüberschreitungsintervall, um die Anwendungssicherheit zu schützen.
seo-description: Alle Authentifizierungstoken, die vom Adobe Primetime DRM SDK generiert werden, haben ein Zeitüberschreitungsintervall, um die Anwendungssicherheit zu schützen.
seo-title: Timeout für Authentifizierungstoken
title: Timeout für Authentifizierungstoken
uuid: 2c2b0dad-0979-4d49-b109-2700ceb4d722
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Timeout für Authentifizierungstoken{#timeout-for-authentication-tokens}

Alle Authentifizierungstoken, die vom Adobe Primetime DRM SDK generiert werden, haben ein Zeitüberschreitungsintervall, um die Anwendungssicherheit zu schützen.

Der Ablauf für das Authentifizierungstoken wird bei der Bearbeitung einer Authentifizierungsanforderung mit dem Primetime DRM SDK angegeben. Nach Ablauf ist das Token nicht mehr gültig und der Benutzer muss sich erneut beim Lizenzserver authentifizieren.

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).
