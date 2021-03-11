---
title: Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional)
description: Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM kann so konfiguriert werden, dass ein Kontakt zu Ihrem eigenen Back-End-Authentifizierungs-/Berechtigungsdienst möglich ist, um Folgendes zu bestimmen:

* Ist dieser Benutzer berechtigt, eine Lizenz zu erwerben?
* Welche Rechte/Einschränkungen sollten in die Lizenz aufgenommen werden?

Primetime Cloud DRM enthält eine Referenz-Implementierung eines Back-End-Authentifizierungs-/Berechtigungsdiensts. Zu Demonstrationszwecken gibt dieser Server Antworten auf BEES-Anfragen &quot;zulassen&quot;aus. Siehe [!DNL BEESServlet.java], um das Serververhalten zu ändern.

>[!NOTE]
>
>Zuvor war dies ein separates Produkt mit dem Namen *Back End Entitlement Server* (BEES), also die Verweise auf BEES in diesem Dokument und in den Quelldateien.

