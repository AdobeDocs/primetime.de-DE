---
title: Verarbeitung von Lizenzrückgabeanfragen
description: Verarbeitung von Lizenzrückgabeanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Verarbeitung von Lizenzrückgabeanfragen{#handling-license-return-requests}

Wenn die Clientanwendung eine Lizenz zurückgeben muss, ruft sie die ActionScript-API DRMManager.returnVoucher() auf, um den Prozess zu initiieren. Diese API kann im Modus quickCommit oder im Modus confirmFirst verwendet werden. Wenn quickCommit auf &quot;true&quot;gesetzt ist, löscht der Client die lokalen Lizenzen sofort, ohne auf die Bestätigung vom Lizenzserver zu warten, dass er die Anfrage zur Rückgabe der Lizenz(en) erhalten hat. Der Adobe Access-Lizenzserver sollte die Anfrage verarbeiten und eine Antwort an den Client senden. Ob der Lizenzserver tatsächlich etwas mit der Anfrage tut (z. B. die Lizenzanzahl für den jeweiligen Benutzer festlegen), hängt vom Lizenzserver ab.

* Die Anfrage-Handler-Klasse ist com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler
* Die Anforderungsmeldungsklasse lautet com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage

Die erforderliche Mindestversion des Adobe Access SDK ist Version 5. Die Anforderungs-URL lautet &quot; `/flashaccess/lreturn/v5`&quot;. Wie bei der Domänenderegistrierung sollte der Server `getRequestPhase()` um festzustellen, ob der Client eine Lizenzrückgabe in der Vorschau anzeigt.
