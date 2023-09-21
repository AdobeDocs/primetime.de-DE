---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Übersicht{#overview}

Der allgemeine Ansatz bei der Verarbeitung von Anforderungen besteht darin, einen Handler zu erstellen, die Anfrage zu analysieren, die Antwortdaten oder den Fehlercode festzulegen und den Handler zu schließen.

Die Basisklasse, die für die Verarbeitung der einzelnen Anfrage-/Antwortakaktionen verwendet wird, lautet `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Eine Instanz der `HandlerConfiguration` -Klasse verwendet wird, um den Handler zu initialisieren. `HandlerConfiguration` speichert Serverkonfigurationsinformationen, einschließlich Transport-Anmeldeinformationen, Toleranz bei Zeitstempeln, Listen für Richtlinienaktualisierungen und Sperrlisten. Der Handler liest die Anfragedaten und analysiert die Anfrage in einer Instanz von `RequestMessageBase`. Der Aufrufer kann die Informationen in der Anfrage untersuchen und entscheiden, ob ein Fehler oder eine erfolgreiche Antwort zurückgegeben wird (Unterklassen von `RequestMessageBase` eine Methode zum Festlegen von Antwortdaten bereitstellen).

Wenn die Anfrage erfolgreich ist, legen Sie die Antwortdaten fest. Rufen Sie andernfalls auf `RequestMessageBase.setErrorData()` bei Fehlschlagen. Beenden Sie die Implementierung immer, indem Sie die `close()` -Methode (es wird empfohlen, dass `close()` in der `finally` Block eines `try` -Anweisung). Siehe `MessageHandlerBase` API-Referenzdokumentation für ein Beispiel zum Aufrufen des Handlers.

>[!NOTE]
>
>HTTP-Status-Code 200 (OK) sollte als Antwort auf alle vom Handler verarbeiteten Anfragen gesendet werden. Wenn der Handler aufgrund eines Serverfehlers nicht erstellt werden konnte, antwortet der Server möglicherweise mit einem anderen Statuscode, z. B. 500 (Interner Serverfehler).

Der Client verwendet die während der Verpackung angegebene Lizenzserver-URL als Basis-URL für alle Anfragen, die an den Lizenzserver gesendet werden. Wenn die Server-URL beispielsweise als &quot;ht&quot;angegeben ist<span></span>tps://licenseserver.com/path&quot;sendet der Client Anfragen an &quot;th&quot;<span></span>tps://licenseserver.com/path/flashaccess/...&quot; In den folgenden Abschnitten finden Sie Details zum spezifischen Pfad, der für die einzelnen Anforderungstypen verwendet wird. Stellen Sie bei der Implementierung Ihres Lizenzservers sicher, dass der Server auf die Pfade reagiert, die für die einzelnen Anforderungstypen erforderlich sind.

Eine Lizenzanfrage kann ein Authentifizierungstoken enthalten. Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anfrage eine `AuthenticationToken` von der `AuthenticationHandler`und das SDK stellt sicher, dass das Token gültig ist, bevor es eine Lizenz erteilt.
