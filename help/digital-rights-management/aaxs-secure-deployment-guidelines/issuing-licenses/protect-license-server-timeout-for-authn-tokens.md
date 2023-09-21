---
title: Zeitüberschreitung für Authentifizierungstoken
description: Zeitüberschreitung für Authentifizierungstoken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Zeitüberschreitung für Authentifizierungstoken{#timeout-for-authentication-tokens}

Alle vom Adobe Access SDK generierten Authentifizierungstoken haben ein Timeout-Intervall, um die Anwendungssicherheit zu schützen. Die Gültigkeit für das Authentifizierungstoken wird bei der Bearbeitung einer Authentifizierungsanfrage mit dem Adobe Access SDK angegeben. Nach Ablauf ist das Authentifizierungstoken nicht mehr gültig und der Benutzer muss sich erneut beim Lizenzserver authentifizieren.

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter AuthenticationHandler im Abschnitt *Adobe Access API-Referenz*.
