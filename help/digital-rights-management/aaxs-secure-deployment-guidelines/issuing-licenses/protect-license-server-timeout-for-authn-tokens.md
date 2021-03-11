---
title: Timeout für Authentifizierungstoken
description: Timeout für Authentifizierungstoken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Timeout für Authentifizierungstoken{#timeout-for-authentication-tokens}

Alle vom Adobe Access SDK generierten Authentifizierungstoken haben ein Zeitüberschreitungsintervall, um die Anwendungssicherheit zu schützen. Der Ablauf für das Authentifizierungstoken wird bei der Bearbeitung einer Authentifizierungsanforderung mit dem Adobe Access SDK angegeben. Nach Ablauf ist das Authentifizierungstoken nicht mehr gültig und der Benutzer muss sich erneut beim Lizenzserver authentifizieren.

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter AuthenticationHandler in der *API-Referenz für den Zugriff auf Adoben*.
