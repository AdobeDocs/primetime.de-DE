---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Übersicht{#overview}

Um eine Lizenz anzufordern, sendet der Client die Metadaten, die während der Verpackung in den Inhalt eingebettet wurden. Der Lizenzserver verwendet die Informationen in den Inhaltsmetadaten, um eine Lizenz zu generieren.

Die `LicenseHandler` liest eine Lizenzanfrage und analysiert die Anfrage. `LicenseHandler`erweitert `BatchHandlerBase` , um Batch-Lizenzanfragen zu berücksichtigen, obwohl diese Funktion derzeit nicht von Adobe Access-Clients unterstützt wird. Die `getRequests()` gibt eine Liste von `LicenseRequestMessage` Objekte. Der Aufrufer sollte durch die `LicenseRequestMessages`und für jede Anfrage entweder eine Lizenz generieren oder einen Fehlercode festlegen (siehe `LicenseRequestMessage` API-Referenzdokumentation für Details). Für jede Lizenzanfrage bestimmt der Server, ob er eine Lizenz ausstellt. Aufruf `LicenseRequestMessage.getContentInfo()` , um Informationen zu erhalten, die aus den Inhaltsmetadaten extrahiert wurden, einschließlich Inhalts-ID, Lizenzkennung und Richtlinien.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Wenn sowohl der Client als auch der Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;Lizenzserver-URL in Metadaten: + &quot;/flashaccess/license/v4&quot;. Wenn die Protokollversion 3 das Maximum ist, das entweder vom Client oder vom Server unterstützt wird, senden Adobe Access-Clients Authentifizierungsanforderungen an &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/license/v3&quot;. Andernfalls werden Authentifizierungsanfragen an &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/license/v1&quot; gesendet

Wenn beim Analysieren der Anforderung ein Fehler auftritt, wird ein `HandlerParsingException` geworfen wird. Diese Ausnahme enthält Fehlerinformationen, die an den Client zurückgegeben werden. Rufen Sie auf, um die Fehlerinformationen abzurufen `HandlerParsingException.getErrorData()`. Wenn beim Generieren einer Lizenz ein Fehler auftritt, weil die Richtlinienanforderungen nicht erfüllt wurden, wird ein `PolicyEvaluationException` geworfen wird. Diese Ausnahme umfasst auch `ErrorData` an den Client zurückgegeben. Siehe API-Dokumentation für `LicenseRequestMessage.generateLicense()` für Details darüber, wie Richtlinien bei der Lizenzerstellung bewertet werden.

Lizenzen und Fehler werden gleichzeitig gesendet, wenn `LicenseHandler.close()` aufgerufen wird.

Ein Gerät kann mehrere Lizenzen für denselben Inhalt (dieselbe Lizenzkennung) haben, jedoch nur eine Lizenz für eine bestimmte Lizenz-ID und Richtlinien-ID. Wenn die neue Lizenz eine Lizenz mit einer doppelten LicenseID/PolicyID erhält, wird die neue Lizenz nur dann die alte ersetzen, wenn das Ausstellungsdatum der neuen Lizenz nach dem Ausstellungsdatum der bestehenden Lizenz liegt. Diese Logik wird verwendet, um in Inhalte eingebettete Lizenzen zu verarbeiten. Daher wird nicht empfohlen, mehr als eine Lizenz mit derselben Richtlinien-ID in einen Inhaltsbereich einzubetten. Dasselbe gilt für Lizenzen, die über die `DRMManager.storeVoucher()` ActionScript3-API; wenn der Client bereits über eine Lizenz mit einem späteren Ausstellungsdatum verfügt, kann die bereitgestellte Lizenz ignoriert werden.
