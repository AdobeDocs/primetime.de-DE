---
seo-title: Bearbeitung von Domänenderegistrierungsanfragen
title: Bearbeitung von Domänenderegistrierungsanfragen
uuid: 6f056b2b-374d-4e4d-926a-68605b2c923b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Bearbeitung von Domänenderegistrierungsanfragen{#handling-domain-de-registration-requests}

Wenn die Clientanwendung eine Domäne verlassen muss, ruft sie die `DRMManager.removeFromDeviceGroup()`ActionScript-API oder die `leaveLicenseDomain()` iOS-API auf, um den Domänenderegistrierungsprozess zu starten. Die Domänenderegistrierung ist ein zweistufiger Prozess. Der Client sendet zuerst eine Vorschau zur Deregistrierung. Der Domänenserver prüft die Anforderung und stellt fest, ob der Client die Domäne verlassen darf (es kann ein Fehler zurückgegeben werden, wenn der Computer derzeit nicht zur Domäne gehört). Bei erfolgreicher Antwort löscht der Client seine Domänenberechtigungen und alle Lizenzen, die für diese Domäne erteilt wurden, und sendet dann eine Deregistrierungsanfrage.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Domänenservers in Metadaten: + &quot;/flashaccess/dereg/v4&quot;. Andernfalls lautet die Anforderungs-URL in den Metadaten &quot;URL des Domänenservers&quot; + &quot;/flashaccess/dereg/v3&quot;

Bei der Verarbeitung von Domänenderegistrierungsanforderungen bestimmt der Server, ob sich der Client in der Vorschau oder der Deregistrierung befindet. `getRequestPhase()` In der Vorschau prüft der Domänenserver die Anforderung und stellt fest, ob der Client die Domäne verlassen darf (die Anforderung kann beispielsweise verweigert werden, wenn der Computer derzeit nicht zur Domäne gehört). In der Entregistrierung zeichnet der Server die Tatsache auf, dass der Computer die Domäne verlassen hat. Der Server wird dringend empfohlen, dieselbe Logik in der Anforderung der Vorschau auszuwerten wie in der Anfrage zur Löschung der Registrierung, um die Wahrscheinlichkeit eines Fehlers in der zweiten Phase zu minimieren.
