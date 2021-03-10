---
title: Aktualisieren von Clients
description: Aktualisieren von Clients
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Aktualisieren von Clients{#upgrading-clients}

Wenn ein FMRMS 1.x-Client einen Adobe Access-Server kontaktiert, muss der Server den Client zur Aktualisierung auffordern.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* Die Anforderungs-URL lautet &quot;*Basis-URL von 1.x content*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

   Im Gegensatz zu anderen Anforderungs-Handlern für den Zugriff auf Adoben bietet dieser Handler keinen Zugriff auf Informationen zu Anforderungen oder erfordert die Einstellung von Antwortdaten. Erstellen Sie eine Instanz von `FMRMSv1RequestHandler` und rufen Sie dann `close()` auf