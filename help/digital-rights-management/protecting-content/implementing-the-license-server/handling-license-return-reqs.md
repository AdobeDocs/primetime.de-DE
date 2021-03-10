---
title: Rückgabeanforderungen für Lizenzen bearbeiten
description: Rückgabeanforderungen für Lizenzen bearbeiten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Verarbeiten von Lizenzrückgabeanforderungen{#handle-license-return-requests}

Wenn die Clientanwendung eine Lizenz zurückgeben muss, ruft sie die ActionScript-API `DRMManager.returnVoucher()` auf, um den Prozess zu starten. Diese API kann im Modus `immediateCommit` oder im Modus `confirmFirst` verwendet werden. Wenn `immediateCommit` auf `true` eingestellt ist, löscht der Client die lokale(n) Lizenz(en) sofort, ohne auf die Bestätigung vom Lizenzserver zu warten, dass er die Anforderung zur Rückgabe der Lizenz(en) erhalten hat. Der Adobe Primetime DRM-Lizenzserver muss die Anforderung bearbeiten und eine Antwort an den Client senden. Ob der Lizenzserver die Anforderung verarbeitet oder nicht, z. B. die Deklaration einer Lizenzanzahl für einen bestimmten Benutzer, wird vom Lizenzserver entschieden.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

Die Mindestversion von `Adobe Primetime DRM` SDK ist Version 5. die Anforderungs-URL lautet &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Wie bei der Domänenderegistrierung verwendet der Server `getRequestPhase()`, um zu ermitteln, ob der Client eine Lizenzrückgabe Vorschau.
