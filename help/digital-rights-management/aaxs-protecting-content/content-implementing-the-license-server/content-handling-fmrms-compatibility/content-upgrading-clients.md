---
title: Aktualisieren von Clients
description: Aktualisieren von Clients
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# Aktualisieren von Clients{#upgrading-clients}

Wenn ein FMRMS 1.x-Client einen Adobe Access-Server kontaktiert, muss der Server den Client zur Aktualisierung auffordern.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* Die Anforderungs-URL lautet &quot;*Basis-URL aus 1.x-Inhalt*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

  Im Gegensatz zu anderen Adobe Access-Anfrage-Handlern bietet dieser Handler keinen Zugriff auf Anfrageinformationen oder erfordert die Festlegung von Antwortdaten. Erstellen Sie eine Instanz der `FMRMSv1RequestHandler`, und rufen Sie dann `close()`
