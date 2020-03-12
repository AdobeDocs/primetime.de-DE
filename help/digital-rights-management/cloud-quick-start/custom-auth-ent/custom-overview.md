---
seo-title: Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional)
title: Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional)
uuid: 8b5e38a5-562c-4781-ac40-4b3d6cdd97fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Übersicht über benutzerdefinierte Authentifizierung/Berechtigungen (optional){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM kann so konfiguriert werden, dass ein Kontakt zu Ihrem eigenen Back-End-Authentifizierungs-/Berechtigungsdienst möglich ist, um Folgendes zu bestimmen:

* Ist dieser Benutzer berechtigt, eine Lizenz zu erwerben?
* Welche Rechte/Einschränkungen sollten in die Lizenz aufgenommen werden?

Primetime Cloud DRM enthält eine Referenz-Implementierung eines Back-End-Authentifizierungs-/Berechtigungsdiensts. Zu Demonstrationszwecken gibt dieser Server Antworten auf BEES-Anfragen &quot;zulassen&quot;aus. Siehe [!DNL BEESServlet.java] Ändern des Serververhaltens.

>[!NOTE]
>
>Zuvor war dies ein separates Produkt mit dem Namen *Back End Entitlement Server* (BEES), also die Verweise auf BEES in diesem Dokument und in den Quelldateien.

