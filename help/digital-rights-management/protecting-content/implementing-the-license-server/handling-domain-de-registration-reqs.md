---
seo-title: Domänenderegistrierungsanfragen bearbeiten
title: Domänenderegistrierungsanfragen bearbeiten
uuid: 80dbbb60-9005-4a3d-86bf-26cdbed86452
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Domänenderegistrierungsanfragen bearbeiten {#handle-domain-de-registration-requests}

Wenn die Clientanwendung eine Domäne verlassen muss, ruft sie die `DRMManager.removeFromDeviceGroup()`ActionScript-API oder die `leaveLicenseDomain()` iOS-API auf, um den Domänenderegistrierungsprozess zu starten. Die Domänenderegistrierung ist ein zweistufiger Prozess. Der Client sendet zuerst eine Vorschau zur Deregistrierung. Der Domänenserver prüft die Anforderung und stellt fest, ob der Client die Domäne verlassen darf. Es kann ein Fehler zurückgegeben werden, wenn der Computer derzeit nicht zur Domäne gehört. Bei erfolgreicher Antwort löscht der Client seine Domänenberechtigungen und alle Lizenzen, die für diese Domäne erteilt wurden. Es wird dann eine Deregistrierungsanfrage gesendet.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Domänenservers in Metadaten: + &quot; [!DNL /flashaccess/dereg/v4]&quot;. Andernfalls lautet die Anforderungs-URL in den Metadaten &quot; + [!DNL /flashaccess/dereg/v3]&quot;

Bei der Verarbeitung von Domänenderegistrierungsanforderungen bestimmt der Server, ob sich der Client in der Vorschau oder der Deregistrierung befindet. `getRequestPhase()` In der Vorschau prüft der Domänenserver die Anforderung und stellt fest, ob der Client die Domäne verlassen darf, da die Anforderung möglicherweise verweigert wird. Beispielsweise kann die Anforderung verweigert werden, wenn der Computer derzeit nicht zur Domäne gehört. In der Entregistrierung zeichnet der Server die Tatsache auf, dass der Computer die Domäne verlassen hat. Der Server wird dringend empfohlen, dieselbe Logik in der Anforderung der Vorschau auszuwerten wie in der Anfrage zur Löschung der Registrierung, um die Wahrscheinlichkeit eines Fehlers in der zweiten Phase zu minimieren.
