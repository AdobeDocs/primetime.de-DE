---
seo-title: Adobe Primetime DRM-Anforderungen verarbeiten
title: Adobe Primetime DRM-Anforderungen verarbeiten
uuid: ee10504d-84f0-472a-b58a-2a87fdeedfc1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---


# Adobe Primetime DRM-Anforderungen verarbeiten {#process-adobe-primetime-drm-requests}

Der allgemeine Ansatz zum Verwalten von Anforderungen besteht darin, einen Handler zu erstellen, die Anforderung zu analysieren, die Antwortdaten oder den Fehlercode festzulegen und den Handler zu schließen.

Die Basisklasse, die für die Verarbeitung der Interaktion einzelner Anforderungen/Antworten verwendet wird, ist `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Zum Initialisieren des Handlers wird eine Instanz der Klasse `HandlerConfiguration` verwendet. `HandlerConfiguration` speichert Serverkonfigurationsinformationen, einschließlich Transport-Anmeldeinformationen, Zeitstempeltoleranz, Listen zur Richtlinienaktualisierung und Listen zum Sperren. Der Handler liest die Anforderungsdaten und analysiert die Anforderung in eine Instanz von  `RequestMessageBase`. Der Aufrufer kann die Informationen in der Anforderung prüfen und entscheiden, ob er einen Fehler oder eine erfolgreiche Antwort zurückgibt (Unterklassen von `RequestMessageBase` bieten eine Methode zum Festlegen von Antwortdaten).

Wenn die Anforderung erfolgreich ist, stellen Sie die Antwortdaten ein. andernfalls `RequestMessageBase.setErrorData()` bei Fehler aufrufen. Beenden Sie die Implementierung immer, indem Sie die `close()`-Methode aufrufen (es wird empfohlen, `close()` im `finally`-Block einer `try`-Anweisung aufzurufen). Ein Beispiel zum Aufrufen des Handlers finden Sie in der API-Referenzdokumentation.`MessageHandlerBase`

>[!NOTE]
>
>HTTP-Statuscode 200 (OK) sollte als Antwort auf alle vom Handler verarbeiteten Anforderungen gesendet werden. Wenn der Handler aufgrund eines Serverfehlers nicht erstellt werden konnte, reagiert der Server möglicherweise mit einem anderen Statuscode, z. B. 500 (Interner Serverfehler).

Der Client verwendet für alle an den Lizenzserver gesendeten Anforderungen die bei der Paketerstellung angegebene Lizenzserver-URL als Basis-URL. Wenn die Server-URL beispielsweise als &lt;[!DNL ht<span></span>tps://licenseserver.com/path] angegeben ist, sendet der Client dann Anforderungen an &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/...]> In den folgenden Abschnitten finden Sie Details zum jeweiligen Pfad, der für jeden Anforderungstyp verwendet wird. Stellen Sie bei der Implementierung des Lizenzservers sicher, dass der Server die für jeden Anforderungstyp erforderlichen Pfade einhält.

Eine Lizenzanforderung kann ein Authentifizierungstoken enthalten. Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anforderung ein `AuthenticationToken` enthalten, das von `AuthenticationHandler` generiert wurde, und das SDK stellt sicher, dass das Token gültig ist, bevor eine Lizenz erteilt wird.

## Verwenden Sie Maschinenkennungen {#use-machine-identifiers}

Alle DRM-Anfragen von Adobe Primetime (mit Ausnahme von Anfragen, die FMRMS-Kompatibilität unterstützen) enthalten Informationen über das Computertoken, das dem Client während der Individualisierung ausgegeben wurde. Das Gerätetoken enthält eine Computer-ID, eine ID, die während der Individualisierung zugewiesen wurde. Mit diesem Bezeichner können Sie die Anzahl der Computer zählen, auf denen ein Benutzer eine Lizenz beantragt oder einer Domäne beigetreten ist.

Sie können einen Bezeichner wie folgt verwenden:

* Die `getUniqueId()`-Methode gibt eine Zeichenfolge zurück, die einem Gerät während der Individualisierung zugewiesen wurde. Sie können die Zeichenfolgen in einer Datenbank speichern und nach Bezeichner suchen. Dieser Bezeichner ändert sich jedoch, wenn der Benutzer die Festplatte neu formatiert und erneut individualisiert. Dieser Bezeichner hat auch einen anderen Wert zwischen Adobe AIR und Adobe Flash Player in verschiedenen Browsern auf demselben Computer.
* Wenn Sie Maschinen genauer zählen möchten, können Sie `getBytes()` verwenden, um den gesamten Bezeichner zu speichern. Um festzustellen, ob der Computer zuvor gesehen wurde, rufen Sie alle Bezeichner für einen Benutzernamen ab und rufen Sie `matches()` auf, um zu prüfen, ob eine Übereinstimmung vorliegt. Da die `matches()`-Methode zum Vergleich der von `MachineId.getBytes` zurückgegebenen Werte verwendet werden muss, ist diese Option nur dann sinnvoll, wenn eine kleine Anzahl von Werten miteinander verglichen werden muss. zum Beispiel die mit einem bestimmten Benutzer verbundenen Computer.

## Benutzerauthentifizierung {#user-authentication}

Eine Adobe Primetime DRM-Anforderung kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anforderung ein `AuthenticationToken` enthalten, das von `AuthenticationHandler` generiert wurde. Wenn Sie auf das Token zugreifen und es überprüfen möchten, müssen Sie `RequestMessageBase.getAuthenticationToken()` verwenden. Um eine Benutzernamens-/Kennwortanfrage auf dem Client zu starten, verwenden Sie die ActionScript- oder iOS-API.`DRMManager.authenticate()`

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mit der ActionScript 3.0-API fest. `DRMManager.setAuthenticationToken` Verwenden Sie `RequestMessageBase.getRawAuthenticationToken()`, um das benutzerdefinierte Authentifizierungstoken abzurufen. Die Serverimplementierung bestimmt, ob das benutzerdefinierte Authentifizierungstoken gültig ist.

## Wiederholungsschutz {#replay-protection}

Zum Schutz der Wiederholung der Wiedergabe möchten Sie möglicherweise überprüfen, ob der Meldungsbezeichner vor kurzem durch Aufruf von `RequestMessageBase.getMessageId()` angezeigt wurde. In diesem Fall versucht ein Angreifer möglicherweise, die Anfrage erneut abzuspielen, was verweigert werden sollte. Um Wiederholungsversuche zu erkennen, kann der Server eine Liste der kürzlich angezeigten Nachrichten-IDs speichern und jede eingehende Anforderung gegen die zwischengespeicherte Liste prüfen. Rufen Sie `HandlerConfiguration.setTimestampTolerance()` auf, um die Dauer der Speicherung der Meldungskennungen zu begrenzen. Wenn diese Eigenschaft festgelegt ist, verweigert das SDK dann alle Anforderungen, die einen Zeitstempel für mehr als die angegebene Anzahl von Sekunden nach der Serverzeit enthalten.

## Rollenerkennung {#rollback-detection}

Für die Rollback-Erkennung müssen einige Verwendungsregeln vorsehen, dass der Client Statusinformationen zur Durchsetzung der Rechte aufbewahrt. Um beispielsweise die Nutzungsregel für das Wiedergabefenster durchzusetzen, speichert der Client das Datum und die Uhrzeit, zu der der Benutzer den Inhalt zum ersten Mal anzeigte. Dieses Ereignis löst den Beginn des Wiedergabefensters aus. Um das Wiedergabefenster sicher durchzusetzen, muss der Server sicherstellen, dass der Beginn nicht gesichert wird, und den Clientstatus wiederherstellen, um die auf dem Client gespeicherte Wiedergabefenster-Zeit zu entfernen. Der Server verfolgt dies, indem er den Wert des Rollback-Zählers des Clients verfolgt.

Für jede Anforderung ruft der Server den Wert des Zählers ab, indem er `RequestMessageBase.getClientState()` aufruft, um das `ClientState`-Objekt abzurufen, und dann `ClientState.getCounter()` aufruft, um den aktuellen Wert des Clientstatuszählers abzurufen. Der Server sollte diesen Wert für jeden Client speichern (verwenden Sie `MachineId.getUniqueId()`, um den Client zu identifizieren, der mit dem Rollback-Zählerwert verknüpft ist), und dann `ClientState.incrementCounter()` aufrufen, um den Zählerwert um 1 zu erhöhen. Wenn der Server erkennt, dass der Zählerwert kleiner als der letzte vom Server angezeigte Wert ist, wurde der Clientstatus möglicherweise zurückgenommen.

Weitere Informationen zur Fehlererkennung im Clientstatus finden Sie in der API-Referenzdokumentation.`ClientState`

## Globale Serverkonfigurationsdaten{#global-server-configuration-data}

Zusätzlich zur vom Lizenzserver verwendeten Konfiguration speichert `HandlerConfiguration` Konfigurationsinformationen, die an den Client gesendet werden können, um zu steuern, wie Lizenzen erzwungen werden. Dies geschieht durch Erstellen einer `ServerConfigData`-Klasse und Aufrufen von `HandlerConfiguration.setServerConfigData()`. Diese Einstellungen gelten nur für Lizenzen, die von diesem Lizenzserver erteilt werden.

Die Uhrzeitrückhaltetoleranz ist eine Eigenschaft, die vom Lizenzserver festgelegt werden kann, um zu steuern, wie der Client Lizenzen durchsetzt. Standardmäßig können Benutzer ihre Computeruhr auf 4 Stunden einstellen, ohne Lizenzen zu ungültigen. Wenn ein Lizenzserveroperator eine andere Einstellung verwenden möchte, kann der neue Wert in der Klasse `ServerConfigData` festgelegt werden. Wenn Sie den Wert einer dieser Einstellungen ändern, stellen Sie sicher, dass Sie die Versionsnummer inkrementieren, indem Sie `setVersion()` aufrufen. Die neuen Werte werden nur dann an den Client gesendet, wenn die Version auf dem Client älter ist als die aktuelle `ServerConfigData`-Version.

## CrossDomain DRM-Richtliniendatei {#crossdomain-drm-policy-file}

Wenn der Lizenzserver auf einer anderen Domäne als die SWF-Datei für die Videowiedergabe gehostet wird, muss eine domänenübergreifende DRM-Richtliniendatei ( [!DNL crossdomain.xml]) erstellt werden, damit die SWF Lizenzen von einem Lizenzserver anfordern kann. Eine domänenübergreifende DRM-Richtliniendatei wird durch eine XML-Datei dargestellt, mit der der Server angeben kann, dass seine Daten und Dokumente für SWF-Dateien verfügbar sind, die von anderen Domänen bereitgestellt werden. Jede SWF-Datei, die von einer Domäne bereitgestellt wird, die in der domänenübergreifenden DRM-Richtliniendatei des Lizenzservers angegeben ist, darf auf Daten oder Assets von diesem Lizenzserver zugreifen.

Adobe empfiehlt, dass Entwickler bei der Bereitstellung der domänenübergreifenden Richtliniendatei die Best Practices befolgen, indem sie nur vertrauenswürdigen Domänen den Zugriff auf den Lizenzserver erlauben und den Zugriff auf den Unterordner der Lizenz auf dem Webserver beschränken.

Weitere Informationen zu domänenübergreifenden DRM-Richtliniendateien finden Sie in den folgenden Verzeichnissen:

* Website-Steuerelemente (DRM-Richtliniendateien)
* Domänenübergreifende DRM-Richtliniendateispezifikation: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)