---
seo-title: Rückgabeanforderungen für Lizenzen bearbeiten
title: Rückgabeanforderungen für Lizenzen bearbeiten
uuid: 994df5af-476a-4ee8-b371-8900241be83d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Rückgabeanforderungen für Lizenzen bearbeiten{#handle-license-return-requests}

Wenn die Clientanwendung eine Lizenz zurückgeben muss, ruft sie die `DRMManager.returnVoucher()` ActionScript-API auf, um den Prozess zu starten. Diese API kann im `immediateCommit` Modus oder im `confirmFirst` Modus verwendet werden. Ist `immediateCommit` `true`dies der Fall, löscht der Client die lokale(n) Lizenz(en) sofort, ohne auf die Bestätigung des Lizenzservers zu warten, dass er die Anforderung zur Rückgabe der Lizenz(en) erhalten hat. Der Adobe Primetime DRM-Lizenzserver muss die Anforderung bearbeiten und eine Antwort an den Client senden. Ob der Lizenzserver die Anforderung verarbeitet oder nicht, z. B. die Deklaration einer Lizenzanzahl für einen bestimmten Benutzer, wird vom Lizenzserver entschieden.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

Die erforderliche SDK- `Adobe Primetime DRM` Version ist mindestens Version 5. die Anforderungs-URL lautet &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Wie bei der Domänenderegistrierung bestimmt der Server, ob der Client eine Lizenzrückgabe Vorschau vornehmen kann. `getRequestPhase()`
