---
title: Firewall-Regeln
description: Firewall-Regeln
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Firewall-Regeln{#firewall-rules}

Um den Zugriff auf den Individualisierungsserver zu sichern, müssen nur bestimmte Anwendungspfade offen gelegt werden. Der Individualisierungsserver muss Anforderungen von Clients an folgende Pfade akzeptieren:

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Dienstpfade, wie z. B. [!DNL /flashaccess/admin/*] (d. h. Status- und Admin-Seiten) dürfen nur von der Firewall aus aufgerufen werden. Auf keinen Teil des Key Generation Servers sollte außerhalb der Firewall zugegriffen werden.
