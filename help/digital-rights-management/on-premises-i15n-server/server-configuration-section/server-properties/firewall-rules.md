---
seo-title: Firewall-Regeln
title: Firewall-Regeln
uuid: f1629ceb-22de-4bb5-b73f-9b874d97ea8b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Firewall-Regeln{#firewall-rules}

Um den Zugriff auf den Individualisierungsserver zu sichern, müssen nur bestimmte Anwendungspfade offen gelegt werden. Der Individualisierungsserver muss Anforderungen von Clients zu folgenden Pfaden akzeptieren:

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Service-Pfade wie [!DNL /flashaccess/admin/*] (z. B. Status- und Admin-Seiten) dürfen nur von der Firewall aus zugänglich sein. Auf keine Teile des Key Generation Servers sollte von außerhalb der Firewall zugegriffen werden.
