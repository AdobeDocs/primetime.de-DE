---
seo-title: Übersicht
title: Übersicht
uuid: 870c32f5-1119-4fec-abed-25e51dd1ebe3
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Übersicht{#overview}

Der allgemeine Ansatz zur Bearbeitung von Anforderungen besteht darin, einen Handler zu erstellen, die Anforderung zu analysieren, die Antwortdaten oder den Fehlercode festzulegen und den Handler zu schließen.

Die Basisklasse, die für die Verarbeitung der Interaktion einzelner Anforderungen/Antworten verwendet wird, ist `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Zum Initialisieren des Handlers wird eine Instanz der Klasse `HandlerConfiguration` verwendet. `HandlerConfiguration` speichert Serverkonfigurationsinformationen, einschließlich Transport-Anmeldeinformationen, Zeitstempeltoleranz, Listen zur Richtlinienaktualisierung und Listen zum Sperren. Der Handler liest die Anforderungsdaten und analysiert die Anforderung in eine Instanz von  `RequestMessageBase`. Der Aufrufer kann die Informationen in der Anforderung prüfen und entscheiden, ob er einen Fehler oder eine erfolgreiche Antwort zurückgibt (Unterklassen von `RequestMessageBase` bieten eine Methode zum Festlegen von Antwortdaten).

Wenn die Anforderung erfolgreich ist, stellen Sie die Antwortdaten ein. andernfalls `RequestMessageBase.setErrorData()` bei Fehler aufrufen. Beenden Sie die Implementierung immer, indem Sie die `close()`-Methode aufrufen (es wird empfohlen, `close()` im `finally`-Block einer `try`-Anweisung aufzurufen). Ein Beispiel zum Aufrufen des Handlers finden Sie in der API-Referenzdokumentation.`MessageHandlerBase`

>[!NOTE]
>
>HTTP-Statuscode 200 (OK) sollte als Antwort auf alle vom Handler verarbeiteten Anforderungen gesendet werden. Wenn der Handler aufgrund eines Serverfehlers nicht erstellt werden konnte, reagiert der Server möglicherweise mit einem anderen Statuscode, z. B. 500 (Interner Serverfehler).

Der Client verwendet für alle an den Lizenzserver gesendeten Anforderungen die bei der Paketerstellung angegebene Lizenzserver-URL als Basis-URL. Wenn die Server-URL beispielsweise als &quot;ht<span></span>tps://licenseserver.com/path&quot;angegeben ist, sendet der Client Anfragen an &quot;ht<span></span>tps://licenseserver.com/path/flashaccess/...&quot;. In den folgenden Abschnitten finden Sie Details zum jeweiligen Pfad, der für die einzelnen Anforderungstypen verwendet wird. Stellen Sie bei der Implementierung des Lizenzservers sicher, dass der Server die für jeden Anforderungstyp erforderlichen Pfade einhält.

Eine Lizenzanforderung kann ein Authentifizierungstoken enthalten. Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anforderung ein `AuthenticationToken` enthalten, das von `AuthenticationHandler` generiert wurde, und das SDK stellt sicher, dass das Token gültig ist, bevor eine Lizenz erteilt wird.
