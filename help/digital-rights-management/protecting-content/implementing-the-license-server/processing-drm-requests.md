---
seo-title: Adobe Primetime DRM-Anforderungen verarbeiten
title: Adobe Primetime DRM-Anforderungen verarbeiten
uuid: ee10504d-84f0-472a-b58a-2a87fdeedfc1
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Adobe Primetime DRM-Anforderungen verarbeiten {#process-adobe-primetime-drm-requests}

Der allgemeine Ansatz zum Verwalten von Anforderungen besteht darin, einen Handler zu erstellen, die Anforderung zu analysieren, die Antwortdaten oder den Fehlercode festzulegen und den Handler zu schließen.

Die Basisklasse, die für die Verarbeitung der Interaktion einzelner Anforderungen/Antworten verwendet wird, ist `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Eine Instanz der `HandlerConfiguration` Klasse wird zum Initialisieren des Handlers verwendet. `HandlerConfiguration` speichert Serverkonfigurationsinformationen, einschließlich Transport-Anmeldeinformationen, Zeitstempeltoleranz, Listen zur Richtlinienaktualisierung und Listen zum Sperren. Der Handler liest die Anforderungsdaten und analysiert die Anforderung in eine Instanz von `RequestMessageBase`. Der Aufrufer kann die Informationen in der Anforderung prüfen und entscheiden, ob ein Fehler oder eine erfolgreiche Antwort zurückgegeben wird (Unterklassen `RequestMessageBase` bieten eine Methode zum Festlegen von Antwortdaten).

Wenn die Anforderung erfolgreich ist, stellen Sie die Antwortdaten ein. andernfalls `RequestMessageBase.setErrorData()` bei Fehler aufrufen. Beenden Sie die Implementierung immer, indem Sie die `close()` Methode aufrufen (es wird empfohlen, dass sie im `close()` Block einer `finally` `try` Anweisung aufgerufen wird). Ein Beispiel zum Aufrufen des Handlers finden Sie in der `MessageHandlerBase` API-Referenzdokumentation.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>HTTP-Statuscode 200 (OK) sollte als Antwort auf alle vom Handler verarbeiteten Anforderungen gesendet werden. Wenn der Handler aufgrund eines Serverfehlers nicht erstellt werden konnte, reagiert der Server möglicherweise mit einem anderen Statuscode, z. B. 500 (Interner Serverfehler).

Der Client verwendet für alle an den Lizenzserver gesendeten Anforderungen die bei der Paketerstellung angegebene Lizenzserver-URL als Basis-URL. Wenn beispielsweise die Server-URL als &lt;[!DNL ht<span></span>tps://licenseserver.com/path]> angegeben ist, sendet der Client dann Anforderungen an &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/...]> In den folgenden Abschnitten finden Sie Einzelheiten zum jeweiligen Pfad, der für jeden Anforderungstyp verwendet wird. Stellen Sie bei der Implementierung des Lizenzservers sicher, dass der Server die für jeden Anforderungstyp erforderlichen Pfade einhält.

Eine Lizenzanforderung kann ein Authentifizierungstoken enthalten. Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, enthält die Anforderung möglicherweise eine `AuthenticationToken` generierte, `AuthenticationHandler`und das SDK stellt sicher, dass das Token gültig ist, bevor eine Lizenz erteilt wird.

## Verwenden Sie die Maschinenkennungen {#use-machine-identifiers}

Alle DRM-Anforderungen von Adobe Primetime (mit Ausnahme von Anforderungen, die FMRMS-Kompatibilität unterstützen) enthalten Informationen über das Computertoken, das dem Client während der Individualisierung ausgegeben wurde. Das Gerätetoken enthält eine Computer-ID, eine ID, die während der Individualisierung zugewiesen wurde. Mit diesem Bezeichner können Sie die Anzahl der Computer zählen, auf denen ein Benutzer eine Lizenz beantragt oder einer Domäne beigetreten ist.

Sie können einen Bezeichner wie folgt verwenden:

* Die `getUniqueId()` Methode gibt eine Zeichenfolge zurück, die einem Gerät während der Individualisierung zugewiesen wurde. Sie können die Zeichenfolgen in einer Datenbank speichern und nach Bezeichner suchen. Dieser Bezeichner ändert sich jedoch, wenn der Benutzer die Festplatte neu formatiert und erneut individualisiert. Dieser Bezeichner hat auch einen anderen Wert zwischen Adobe AIR und Adobe Flash Player in verschiedenen Browsern auf demselben Computer.
* Wenn Sie Maschinen genauer zählen möchten, können Sie den gesamten Bezeichner `getBytes()` speichern. Um festzustellen, ob der Computer zuvor gesehen wurde, rufen Sie alle Bezeichner für einen Benutzernamen ab und prüfen Sie, ob eine Übereinstimmung vorliegt. `matches()` Da die `matches()` `MachineId.getBytes`Methode zum Vergleich der zurückgegebenen Werte verwendet werden muss, ist diese Option nur dann praktisch, wenn eine kleine Anzahl von Werten miteinander verglichen werden kann. zum Beispiel die mit einem bestimmten Benutzer verbundenen Computer.

## Benutzerauthentifizierung {#user-authentication}

Eine Adobe Primetime-DRM-Anforderung kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anforderung eine `AuthenticationToken` durch die `AuthenticationHandler`. Wenn Sie auf das Token zugreifen und es überprüfen möchten, müssen Sie es verwenden `RequestMessageBase.getAuthenticationToken()`. Verwenden Sie die `DRMManager.authenticate()` ActionScript- oder iOS-API, um eine Benutzername-/Kennwortanforderung auf dem Client zu starten.

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mithilfe der `DRMManager.setAuthenticationToken` ActionScript 3.0-API fest. Verwenden Sie `RequestMessageBase.getRawAuthenticationToken()` das benutzerdefinierte Authentifizierungstoken. Die Serverimplementierung bestimmt, ob das benutzerdefinierte Authentifizierungstoken gültig ist.

## Wiederholungsschutz {#replay-protection}

Zum Schutz der Wiederholung der Wiedergabe möchten Sie möglicherweise überprüfen, ob der Benachrichtigungsbezeichner vor kurzem durch Aufruf angezeigt wurde `RequestMessageBase.getMessageId()`. In diesem Fall versucht ein Angreifer möglicherweise, die Anfrage erneut abzuspielen, was verweigert werden sollte. Um Wiederholungsversuche zu erkennen, kann der Server eine Liste der kürzlich angezeigten Nachrichten-IDs speichern und jede eingehende Anforderung gegen die zwischengespeicherte Liste prüfen. Rufen Sie `HandlerConfiguration.setTimestampTolerance()`an, um die Dauer der Speicherung der Meldungskennungen zu begrenzen. Wenn diese Eigenschaft festgelegt ist, verweigert das SDK dann alle Anforderungen, die einen Zeitstempel für mehr als die angegebene Anzahl von Sekunden nach der Serverzeit enthalten.

## Rollenerkennung {#rollback-detection}

Für die Rollback-Erkennung müssen einige Verwendungsregeln vorsehen, dass der Client Statusinformationen zur Durchsetzung der Rechte aufbewahrt. Um beispielsweise die Nutzungsregel für das Wiedergabefenster durchzusetzen, speichert der Client das Datum und die Uhrzeit, zu der der Benutzer den Inhalt zum ersten Mal anzeigte. Dieses Ereignis löst den Beginn des Wiedergabefensters aus. Um das Wiedergabefenster sicher durchzusetzen, muss der Server sicherstellen, dass der Beginn nicht gesichert wird, und den Clientstatus wiederherstellen, um die auf dem Client gespeicherte Wiedergabefenster-Zeit zu entfernen. Der Server verfolgt dies, indem er den Wert des Rollback-Zählers des Clients verfolgt.

Für jede Anforderung ruft der Server den Wert des Zählers ab, indem er `RequestMessageBase.getClientState()` zum Abrufen des `ClientState` Objekts aufruft und dann den aktuellen Wert des Clientstatuszählers abruft `ClientState.getCounter()` . Der Server sollte diesen Wert für jeden Client speichern ( `MachineId.getUniqueId()` um den Client zu identifizieren, der mit dem Rollback-Zählerwert verbunden ist) und dann aufrufen, den Zählerwert um 1 zu erhöhen `ClientState.incrementCounter()` . Wenn der Server erkennt, dass der Zählerwert kleiner als der letzte vom Server angezeigte Wert ist, wurde der Clientstatus möglicherweise zurückgenommen.

Weitere Informationen zur Fehlererkennung im Clientstatus finden Sie in der `ClientState` API-Referenzdokumentation.

## Globale Serverkonfigurationsdaten{#global-server-configuration-data}

Neben der vom Lizenzserver verwendeten Konfiguration werden `HandlerConfiguration` Konfigurationsinformationen gespeichert, die an den Client gesendet werden können, um zu steuern, wie Lizenzen erzwungen werden. Dies geschieht durch Erstellen einer `ServerConfigData` Klasse und Aufrufen `HandlerConfiguration.setServerConfigData()`. Diese Einstellungen gelten nur für Lizenzen, die von diesem Lizenzserver erteilt werden.

Die Uhrzeitrückhaltetoleranz ist eine Eigenschaft, die vom Lizenzserver festgelegt werden kann, um zu steuern, wie der Client Lizenzen durchsetzt. Standardmäßig können Benutzer ihre Computeruhr auf 4 Stunden einstellen, ohne Lizenzen zu ungültigen. Wenn ein Lizenzserveroperator eine andere Einstellung verwenden möchte, kann der neue Wert in der `ServerConfigData` Klasse festgelegt werden. Wenn Sie den Wert einer dieser Einstellungen ändern, stellen Sie sicher, dass Sie die Versionsnummer durch Aufruf erhöhen `setVersion()`. Die neuen Werte werden nur dann an den Client gesendet, wenn die Version auf dem Client älter als die aktuelle `ServerConfigData` Version ist.

## Cross-Domain DRM-Richtliniendatei {#crossdomain-drm-policy-file}

Wenn der Lizenzserver auf einer anderen Domäne als die SWF-Datei für die Videowiedergabe gehostet wird, muss eine domänenübergreifende DRM-Richtliniendatei ( [!DNL crossdomain.xml]) erstellt werden, damit die SWF Lizenzen von einem Lizenzserver anfordern kann. Eine domänenübergreifende DRM-Richtliniendatei wird durch eine XML-Datei dargestellt, mit der der Server angeben kann, dass seine Daten und Dokumente für SWF-Dateien verfügbar sind, die von anderen Domänen bereitgestellt werden. Jede SWF-Datei, die von einer Domäne bereitgestellt wird, die in der domänenübergreifenden DRM-Richtliniendatei des Lizenzservers angegeben ist, darf auf Daten oder Assets von diesem Lizenzserver zugreifen.

Adobe empfiehlt Entwicklern, bei der Bereitstellung der domänenübergreifenden Richtliniendatei die Best Practices zu befolgen, indem sie nur vertrauenswürdigen Domänen den Zugriff auf den Lizenzserver erlauben und den Zugriff auf den Unterordner der Lizenz auf dem Webserver beschränken.

Weitere Informationen zu domänenübergreifenden DRM-Richtliniendateien finden Sie in den folgenden Verzeichnissen:

* Website-Steuerelemente (DRM-Richtliniendateien)
* Domänenübergreifende DRM-Richtliniendateispezifikation: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)