---
title: Domänenderegistrierungsanfragen verarbeiten
description: Domänenderegistrierungsanfragen verarbeiten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Domänenderegistrierungsanfragen verarbeiten {#handle-domain-de-registration-requests}

Wenn die Client-Anwendung eine Domäne verlassen muss, wird die `DRMManager.removeFromDeviceGroup()`ActionScript-API oder die `leaveLicenseDomain()` iOS-API zum Initiieren der Domänenderegistrierung. Die Domänenderegistrierung ist ein zweistufiger Prozess. Der Client sendet zunächst eine Vorschauanforderung zur Deregistrierung. Der Domain-Server prüft die Anfrage und bestimmt, ob der Client die Domäne verlassen darf. Wenn der Computer derzeit nicht Teil der Domäne ist, kann ein Fehler zurückgegeben werden. Nach einer erfolgreichen Antwort löscht der Client seine Domain-Anmeldeinformationen und alle Lizenzen, die für diese Domäne ausgestellt wurden. Danach wird eine Abmeldeanfrage gesendet.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Wenn sowohl der Client als auch der Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;Domain Server URL in metadata: + &quot;. [!DNL /flashaccess/dereg/v4]&quot;. Andernfalls lautet die Anforderungs-URL Domain Server URL in Metadaten&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;

Bei der Verarbeitung von Domänenderegistrierungsanfragen verwendet der Server `getRequestPhase()` , um zu bestimmen, ob sich der Client in der Vorschau- oder Abmeldephase befindet. In der Vorschauphase prüft der Domain-Server die Anfrage und bestimmt, ob der Client die Domäne verlassen darf, da die Anfrage verweigert werden kann. Beispielsweise kann die Anfrage verweigert werden, wenn der Computer derzeit nicht zur Domäne gehört. In der Abmeldephase zeichnet der Server die Tatsache auf, dass der Computer die Domäne verlassen hat. Es wird dringend empfohlen, dass der Server dieselbe Logik in der Vorschauanforderung wie in der eigentlichen Registrierungsanfrage auswertet, um die Wahrscheinlichkeit eines Fehlschlagens der zweiten Phase zu minimieren.
