---
title: Umgang mit Domänenderegistrierungsanfragen
description: Umgang mit Domänenderegistrierungsanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Umgang mit Domänenderegistrierungsanfragen{#handling-domain-de-registration-requests}

Wenn die Client-Anwendung eine Domäne verlassen muss, wird die `DRMManager.removeFromDeviceGroup()`ActionScript-API oder die `leaveLicenseDomain()` iOS-API zum Initiieren der Domänenderegistrierung. Die Domänenderegistrierung ist ein zweistufiger Prozess. Der Client sendet zunächst eine Vorschauanforderung zur Deregistrierung. Der Domain-Server prüft die Anfrage und ermittelt, ob der Client die Domäne verlassen darf (es kann ein Fehler zurückgegeben werden, wenn der Computer derzeit nicht zur Domäne gehört). Bei einer erfolgreichen Antwort löscht der Client seine Domain-Anmeldeinformationen und alle Lizenzen, die für diese Domäne ausgestellt wurden, und sendet dann eine Anfrage zur Aufhebung der Registrierung.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Wenn sowohl der Client als auch der Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;Domain Server URL in metadata: + &quot;/flashaccess/dereg/v4&quot;. Andernfalls lautet die Anforderungs-URL Domain Server URL in den Metadaten &quot;+ &quot;/flashaccess/dereg/v3&quot;

Bei der Verarbeitung von Domänenderegistrierungsanfragen verwendet der Server `getRequestPhase()` , um zu bestimmen, ob sich der Client in der Vorschau- oder Abmeldephase befindet. In der Vorschauphase prüft der Domain-Server die Anfrage und bestimmt, ob der Client die Domäne verlassen darf (die Anfrage kann beispielsweise verweigert werden, wenn der Computer derzeit nicht zur Domäne gehört). In der Abmeldephase zeichnet der Server die Tatsache auf, dass der Computer die Domäne verlassen hat. Es wird dringend empfohlen, dass der Server dieselbe Logik in der Vorschauanforderung wie in der eigentlichen Registrierungsanfrage auswertet, um die Wahrscheinlichkeit eines Fehlschlagens der zweiten Phase zu minimieren.
