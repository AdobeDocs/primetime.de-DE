---
title: Firewall-Regeln
description: Firewall-Regeln
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# Firewall-Regeln{#firewall-rules}

Um den Zugriff auf den Individualisierungsserver zu sichern, müssen nur bestimmte Anwendungspfade offen gelegt werden. Der Individualisierungsserver muss Anforderungen von Clients zu folgenden Pfaden akzeptieren:

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Dienstpfade wie [!DNL /flashaccess/admin/*] (d.h. Status- und Admin-Seiten) dürfen nur von der Firewall aus aufgerufen werden. Auf keine Teile des Key Generation Servers sollte von außerhalb der Firewall zugegriffen werden.
