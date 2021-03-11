---
title: Bearbeitung von Domänenderegistrierungsanfragen
description: Bearbeitung von Domänenderegistrierungsanfragen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Bearbeitung von Domänenderegistrierungsanfragen{#handling-domain-de-registration-requests}

Wenn die Clientanwendung eine Domäne verlassen muss, ruft sie die `DRMManager.removeFromDeviceGroup()`ActionScript-API oder die `leaveLicenseDomain()` iOS-API auf, um den Domänenderegistrierungsprozess zu starten. Die Domänenderegistrierung ist ein zweistufiger Prozess. Der Client sendet zuerst eine Vorschau zur Deregistrierung. Der Domänenserver prüft die Anforderung und stellt fest, ob der Client die Domäne verlassen darf (es kann ein Fehler zurückgegeben werden, wenn der Computer derzeit nicht zur Domäne gehört). Bei erfolgreicher Antwort löscht der Client seine Domänenberechtigungen und alle Lizenzen, die für diese Domäne erteilt wurden, und sendet dann eine Deregistrierungsanfrage.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Domänenservers in Metadaten: + &quot;/flashaccess/dereg/v4&quot;. Andernfalls lautet die Anforderungs-URL in den Metadaten &quot;URL des Domänenservers&quot; + &quot;/flashaccess/dereg/v3&quot;

Bei der Verarbeitung von Domänenderegistrierungsanforderungen verwendet der Server `getRequestPhase()`, um zu ermitteln, ob sich der Client in der Vorschau- oder Deregistrierungsphase befindet. In der Vorschau prüft der Domänenserver die Anforderung und stellt fest, ob der Client die Domäne verlassen darf (die Anforderung kann beispielsweise verweigert werden, wenn der Computer derzeit nicht zur Domäne gehört). In der Entregistrierung zeichnet der Server die Tatsache auf, dass der Computer die Domäne verlassen hat. Der Server wird dringend empfohlen, dieselbe Logik in der Anforderung der Vorschau auszuwerten wie in der Anfrage zur Löschung der Registrierung, um die Wahrscheinlichkeit eines Fehlers in der zweiten Phase zu minimieren.
