---
title: Verarbeitung von Lizenzrückgabeanfragen
description: Verarbeitung von Lizenzrückgabeanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verarbeitung von Lizenzrückgabeanfragen{#handle-license-return-requests}

Wenn die Client-Anwendung eine Lizenz zurückgeben muss, ruft sie die `DRMManager.returnVoucher()` ActionScript-API zum Initiieren des Prozesses. Diese API kann in einer `immediateCommit` oder einen `confirmFirst` -Modus. Wenn `immediateCommit` auf `true`, löscht der Client dann die lokale(n) Lizenz(en) sofort, ohne auf die Bestätigung vom Lizenzserver zu warten, dass er die Anfrage zur Rückgabe der Lizenz(en) erhalten hat. Der Adobe Primetime DRM-Lizenzserver sollte die Anfrage verarbeiten und eine Antwort an den Client senden. Ob der Lizenzserver die Anforderung verarbeitet, z. B. die Lizenzanzahl für einen bestimmten Benutzer festlegt, wird vom Lizenzserver festgelegt.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

Das Minimum `Adobe Primetime DRM` Die erforderliche SDK-Version ist Version 5. Die Anfrage-URL lautet &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Wie bei der Domänenderegistrierung verwendet der Server `getRequestPhase()` , um zu bestimmen, ob der Client eine Lizenzrückgabe in der Vorschau anzeigen kann.
