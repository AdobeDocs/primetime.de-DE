---
seo-title: Aktualisieren von Clients
title: Aktualisieren von Clients
uuid: 9c9bc7da-2a97-4659-945a-554d778d30a3
translation-type: tm+mt
source-git-commit: 5cf90a75d8805fb64d7d145722ad10a1ce77a14d

---


# Aktualisieren von Clients{#upgrading-clients}

Wenn ein FMRMS 1.x-Client einen Adobe Access-Server kontaktiert, muss der Server den Client zur Aktualisierung auffordern.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* Die Anforderungs-URL lautet &quot;*Basis-URL von 1.x-Inhalt*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

   Im Gegensatz zu anderen Adobe Access-Anforderungs-Handlern bietet dieser Handler keinen Zugriff auf Informationen zu Anforderungen oder erfordert die Einstellung von Antwortdaten. Erstellen Sie eine Instanz der `FMRMSv1RequestHandler`und rufen Sie dann `close()`