---
seo-title: Bearbeitung von Lizenzrückgabeanforderungen
title: Bearbeitung von Lizenzrückgabeanforderungen
uuid: d184faea-88cb-44f3-a253-e5314d577f17
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Verarbeitung von Lizenzrückgabeanforderungen{#handling-license-return-requests}

Wenn die Clientanwendung eine Lizenz zurückgeben muss, ruft sie die ActionScript-API DRMManager.returnVoucher() auf, um den Prozess zu starten. Diese API kann im Modus &quot;directCommit&quot;oder im Modus &quot;verifyFirst&quot;verwendet werden. Wenn der Wert für directCommit auf true gesetzt ist, löscht der Client die lokale(n) Lizenz(en) sofort, ohne auf die Bestätigung des Lizenzservers zu warten, dass er die Anforderung zur Rückgabe der Lizenz(en) erhalten hat. Der Lizenzserver für Adobe Access sollte die Anforderung verarbeiten und eine Antwort an den Client senden. Ob der Lizenzserver tatsächlich etwas mit der Anforderung macht (z. B. eine Lizenzanzahl für den jeweiligen Benutzer festlegen), hängt vom Lizenzserver ab.

* Die Anforderungs-Handler-Klasse lautet com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler
* Die Anforderungsmeldungsklasse lautet com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage

Für Adobe Access SDK ist mindestens Version 5 erforderlich. Die Anforderungs-URL lautet &quot; `/flashaccess/lreturn/v5`&quot;. Wie bei der Domänenderegistrierung sollte der Server `getRequestPhase()` verwenden, um festzustellen, ob der Client eine Lizenzrückgabe in der Vorschau anzeigt.
