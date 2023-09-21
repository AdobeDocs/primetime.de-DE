---
title: Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional)
description: Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM kann so konfiguriert werden, dass Sie zu Ihrem eigenen Back-End-Authentifizierungs-/Berechtigungsdienst gelangen, um Folgendes zu bestimmen:

* Ist dieser Benutzer berechtigt, eine Lizenz zu erwerben?
* Welche Rechte/Einschränkungen sollten in die Lizenz aufgenommen werden?

Primetime Cloud DRM enthält eine Referenzimplementierung eines Back-End-Authentifizierungs-/Berechtigungsdiensts. Zu Demonstrationszwecken gibt dieser Server Antworten auf BEES-Anfragen &quot;allow&quot;aus. Siehe [!DNL BEESServlet.java] , um das Serververhalten zu ändern.

>[!NOTE]
>
>Zuvor war dies ein separates Produkt namens *Back End Entitlement Server* (BEES), also die Verweise auf BEES in diesem Dokument und in den Quelldateien.
