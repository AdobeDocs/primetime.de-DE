---
seo-title: Übersicht
title: Übersicht
uuid: d3bfa65b-2360-4843-b59e-71451fa62a2c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Übersicht{#overview}

Um eine Lizenz anzufordern, sendet der Client die Metadaten, die während der Verpackung in den Inhalt eingebettet wurden. Der Lizenzserver verwendet die Informationen in den Inhaltsmetadaten, um eine Lizenz zu generieren.

`LicenseHandler` liest eine Lizenzanforderung und analysiert die Anforderung. `LicenseHandler`erweitert  `BatchHandlerBase` werden, um Anforderungen von Stapellizenzen zu erfüllen, obwohl diese Funktion derzeit nicht von Adobe Access-Clients unterstützt wird. Die `getRequests()`-Methode gibt eine Liste von `LicenseRequestMessage`-Objekten zurück. Der Aufrufer sollte die `LicenseRequestMessages` durchlaufen und für jede Anforderung entweder eine Lizenz generieren oder einen Fehlercode einstellen (weitere Informationen finden Sie in der `LicenseRequestMessage`-API-Referenzdokumentation). Für jede Lizenzanforderung bestimmt der Server, ob eine Lizenz ausgegeben wird. Rufen Sie `LicenseRequestMessage.getContentInfo()` auf, um Informationen abzurufen, die aus den Inhaltsmetadaten extrahiert wurden, einschließlich der Inhalts-ID, der Lizenz-ID und der Richtlinien.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten: + &quot;/flashaccess/license/v4&quot;. Wenn die Protokollversion 3 die vom Client oder Server maximal unterstützte Version ist, senden Adobe Access-Clients Authentifizierungsanforderungen an &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/license/v3&quot;. Andernfalls werden Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot;/flashaccess/license/v1&quot; gesendet

Tritt bei der Analyse der Anforderung ein Fehler auf, wird ein `HandlerParsingException` ausgegeben. Diese Ausnahme enthält Fehlerinformationen, die an den Client zurückgegeben werden. Rufen Sie zum Abrufen der Fehlerinformationen `HandlerParsingException.getErrorData()` auf. Wenn beim Generieren einer Lizenz ein Fehler auftritt, weil die Richtlinienanforderungen nicht erfüllt wurden, wird ein `PolicyEvaluationException`-Fehler ausgegeben. Diese Ausnahme umfasst auch `ErrorData`, die an den Client zurückgegeben werden. Weitere Informationen dazu, wie Richtlinien während der Lizenzerstellung bewertet werden, finden Sie in der API-Dokumentation für `LicenseRequestMessage.generateLicense()`.

Lizenzen und Fehler werden gleichzeitig gesendet, wenn `LicenseHandler.close()` aufgerufen wird.

Ein Gerät kann über mehrere Lizenzen für denselben Inhalt verfügen (gleiche Lizenz-ID), jedoch nur eine Lizenz für eine bestimmte Lizenz-ID und Richtlinien-ID besitzen. Wenn eine Lizenz mit einer LicenseID/PolicyID des Duplikats vorliegt, ersetzt die neue Lizenz die alte nur, wenn das Ausstellungsdatum der neuen Lizenz nach dem Ausstellungsdatum der Lizenz liegt. Diese Logik wird zur Verarbeitung von Lizenzen verwendet, die in Inhalte eingebettet sind. Daher wird nicht empfohlen, mehr als eine Lizenz mit derselben Richtlinien-ID in einen Inhaltsabschnitt einzubetten. Die gleiche Logik gilt für Lizenzen, die über die `DRMManager.storeVoucher()` ActionScript3-API an den Client weitergeleitet werden. Wenn der Kunde bereits über eine Lizenz mit einem späteren Ausgabedatum verfügt, kann die bereitgestellte Lizenz ignoriert werden.
