---
seo-title: Aktualisieren von Clients
title: Aktualisieren von Clients
uuid: 9c9bc7da-2a97-4659-945a-554d778d30a3
translation-type: tm+mt
source-git-commit: 5cf90a75d8805fb64d7d145722ad10a1ce77a14d
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Aktualisieren von Clients{#upgrading-clients}

Wenn ein FMRMS 1.x-Client einen Adobe Access-Server kontaktiert, muss der Server den Client zur Aktualisierung auffordern.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* Die Anforderungs-URL lautet &quot;*Basis-URL von 1.x content*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

   Im Gegensatz zu anderen Anforderungs-Handlern für den Zugriff auf Adoben bietet dieser Handler keinen Zugriff auf Informationen zu Anforderungen oder erfordert die Einstellung von Antwortdaten. Erstellen Sie eine Instanz von `FMRMSv1RequestHandler` und rufen Sie dann `close()` auf