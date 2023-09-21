---
title: Adobe Primetime DRM-Anforderungen verarbeiten
description: Adobe Primetime DRM-Anforderungen verarbeiten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Adobe Primetime DRM-Anforderungen verarbeiten {#process-adobe-primetime-drm-requests}

Der allgemeine Ansatz zum Verwalten von Anforderungen besteht darin, einen Handler zu erstellen, die Anfrage zu analysieren, die Antwortdaten oder den Fehlercode festzulegen und den Handler zu schließen.

Die Basisklasse, die für die Verarbeitung der einzelnen Anfrage-/Antwortakaktionen verwendet wird, lautet `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Eine Instanz der `HandlerConfiguration` -Klasse verwendet wird, um den Handler zu initialisieren. `HandlerConfiguration` speichert Serverkonfigurationsinformationen, einschließlich Transport-Anmeldeinformationen, Toleranz bei Zeitstempeln, Listen für Richtlinienaktualisierungen und Sperrlisten. Der Handler liest die Anfragedaten und analysiert die Anfrage in einer Instanz von `RequestMessageBase`. Der Aufrufer kann die Informationen in der Anfrage untersuchen und entscheiden, ob ein Fehler oder eine erfolgreiche Antwort zurückgegeben wird (Unterklassen von `RequestMessageBase` eine Methode zum Festlegen von Antwortdaten bereitstellen).

Wenn die Anfrage erfolgreich ist, legen Sie die Antwortdaten fest. Rufen Sie andernfalls auf `RequestMessageBase.setErrorData()` bei Fehlschlagen. Beenden Sie die Implementierung immer, indem Sie die `close()` -Methode (es wird empfohlen, dass `close()` in der `finally` Block eines `try` -Anweisung). Siehe `MessageHandlerBase` API-Referenzdokumentation für ein Beispiel zum Aufrufen des Handlers.

>[!NOTE]
>
>HTTP-Status-Code 200 (OK) sollte als Antwort auf alle vom Handler verarbeiteten Anfragen gesendet werden. Wenn der Handler aufgrund eines Serverfehlers nicht erstellt werden konnte, antwortet der Server möglicherweise mit einem anderen Statuscode, z. B. 500 (Interner Serverfehler).

Der Client verwendet die während der Verpackung angegebene Lizenzserver-URL als Basis-URL für alle Anfragen, die an den Lizenzserver gesendet werden. Wenn die Server-URL beispielsweise als &lt;[!DNL ht<span></span>tps://licenseserver.com/path]>, sendet der Client dann Anforderungen an &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/..]> In den folgenden Abschnitten finden Sie Details zum spezifischen Pfad, der für die einzelnen Anforderungstypen verwendet wird. Stellen Sie bei der Implementierung Ihres Lizenzservers sicher, dass der Server auf die Pfade reagiert, die für die einzelnen Anforderungstypen erforderlich sind.

Eine Lizenzanfrage kann ein Authentifizierungstoken enthalten. Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anfrage eine `AuthenticationToken` von der `AuthenticationHandler`und das SDK stellt sicher, dass das Token gültig ist, bevor es eine Lizenz erteilt.

## Verwenden von Maschinenkennungen {#use-machine-identifiers}

Alle Adobe Primetime DRM-Anfragen (mit Ausnahme von Anfragen, die die FMRMS-Kompatibilität unterstützen) enthalten Informationen über das Computer-Token, das dem Client während der Individualisierung zugewiesen wurde. Das Computer-Token enthält eine Computer-ID, eine Kennung, die während der Individualisierung zugewiesen wurde. Mit dieser Kennung können Sie die Anzahl der Computer zählen, von denen aus ein Benutzer eine Lizenz angefordert oder einer Domäne beigetreten ist.

Sie können eine Kennung wie folgt verwenden:

* Die `getUniqueId()` gibt eine Zeichenfolge zurück, die einem Gerät während der Individualisierung zugewiesen wurde. Sie können die Zeichenfolgen in einer Datenbank speichern und nach Kennung suchen. Diese Kennung ändert sich jedoch, wenn der Benutzer die Festplatte neu formatiert und erneut individualisiert. Diese Kennung hat auch einen anderen Wert zwischen Adobe AIR und Adobe Flash Player in verschiedenen Browsern auf demselben Computer.
* Wenn Sie Maschinen genauer zählen möchten, können Sie `getBytes()` zum Speichern der gesamten Kennung. Um festzustellen, ob der Computer zuvor gesehen wurde, rufen Sie alle Kennungen für einen Benutzernamen ab und rufen Sie auf `matches()` , um zu überprüfen, ob eine Übereinstimmung vorliegt. Da die `matches()` -Methode verwendet werden, um die von `MachineId.getBytes`, ist diese Option nur praktisch, wenn eine kleine Anzahl von Werten verglichen werden muss, z. B. die mit einem bestimmten Benutzer verbundenen Maschinen.

## Benutzerauthentifizierung {#user-authentication}

Eine DRM-Anfrage für Adobe Primetime kann ein Authentifizierungstoken enthalten.

Wenn Benutzername/Kennwort-Authentifizierung verwendet wurde, kann die Anfrage eine `AuthenticationToken` von der `AuthenticationHandler`. Wenn Sie auf das Token zugreifen und es überprüfen möchten, müssen Sie `RequestMessageBase.getAuthenticationToken()`. Verwenden Sie zum Initiieren einer Anfrage zum Benutzernamen/Kennwort auf dem Client die `DRMManager.authenticate()` ActionScript oder iOS-API.

Wenn Client und Server einen benutzerdefinierten Authentifizierungsmechanismus verwenden, ruft der Client über einen anderen Kanal ein Authentifizierungstoken ab und legt das benutzerdefinierte Authentifizierungstoken mithilfe des `DRMManager.setAuthenticationToken` ActionScript 3.0-API. Verwendung `RequestMessageBase.getRawAuthenticationToken()` , um das benutzerdefinierte Authentifizierungstoken abzurufen. Die Serverimplementierung bestimmt, ob das benutzerdefinierte Authentifizierungstoken gültig ist.

## Wiederholungsschutz {#replay-protection}

Zum Schutz der Wiederholung möchten Sie möglicherweise überprüfen, ob die Nachrichtenkennung kürzlich angezeigt wurde, indem Sie `RequestMessageBase.getMessageId()`. Wenn ja, könnte ein Angreifer versuchen, die Anfrage erneut auszuführen, was verweigert werden sollte. Um Wiederholungsversuche zu erkennen, kann der Server eine Liste der kürzlich angezeigten Nachrichten-IDs speichern und jede eingehende Anfrage mit der zwischengespeicherten Liste vergleichen. Rufen Sie auf, um die Dauer der Speicherung der Nachrichtenbezeichner zu begrenzen. `HandlerConfiguration.setTimestampTolerance()`. Wenn diese Eigenschaft festgelegt ist, verweigert das SDK dann alle Anfragen, die einen Zeitstempel für mehr als die angegebene Anzahl von Sekunden Serverzeit enthalten.

## Rollenerkennung {#rollback-detection}

Für die Rollback-Erkennung müssen einige Nutzungsregeln vorsehen, dass der Client Statusinformationen für die Durchsetzung der Rechte aufbewahrt. Um beispielsweise die Nutzungsregel für das Wiedergabefenster durchzusetzen, speichert der Client das Datum und die Uhrzeit, zu der der Benutzer mit der Anzeige des Inhalts begonnen hat. Dieses Ereignis Trigger den Start des Wiedergabefensters. Um das Wiedergabefenster sicher zu erzwingen, muss der Server sicherstellen, dass der Benutzer keine Sicherung durchführt und den Clientstatus wiederherstellt, um die auf dem Client gespeicherte Startzeit des Wiedergabefensters zu entfernen. Der Server verfolgt dies, indem er den Wert des Rollback-Zählers des Clients verfolgt.

Für jede Anfrage ruft der Server den Wert des Zählers ab, indem er `RequestMessageBase.getClientState()` um die `ClientState` -Objekt, dann aufrufen `ClientState.getCounter()` , um den aktuellen Wert des Kundenstatuszählers abzurufen. Der Server sollte diesen Wert für jeden Client speichern (verwenden Sie `MachineId.getUniqueId()` , um den mit dem Rollback-Zählerwert verknüpften Client zu identifizieren), und rufen Sie dann `ClientState.incrementCounter()` , um den Zählerwert um 1 zu erhöhen. Wenn der Server erkennt, dass der Zählerwert kleiner als der vom Server zuletzt angezeigte Wert ist, wurde der Clientstatus möglicherweise zurückgesetzt.

Siehe `ClientState` API-Referenzdokumentation für weitere Informationen zur Fehlererkennung für den Clientstatus.

## Globale Server-Konfigurationsdaten{#global-server-configuration-data}

Zusätzlich zur Konfiguration, die vom Lizenzserver verwendet wird, `HandlerConfiguration` speichert Konfigurationsinformationen, die an den Client gesendet werden können, um zu steuern, wie Lizenzen durchgesetzt werden. Erstellen Sie dazu eine `ServerConfigData` -Klasse und Aufrufen `HandlerConfiguration.setServerConfigData()`. Diese Einstellungen gelten nur für von diesem Lizenzserver erteilte Lizenzen.

Die Uhrzeitwindback-Toleranz ist eine Eigenschaft, die vom Lizenzserver festgelegt werden kann, um zu steuern, wie der Client Lizenzen erzwingt. Standardmäßig können Benutzer ihre Maschinenuhr auf 4 Stunden zurücksetzen, ohne Lizenzen ungültig zu machen. Wenn ein Lizenzserver-Benutzer eine andere Einstellung verwenden möchte, kann der neue Wert im `ServerConfigData` -Klasse. Wenn Sie den Wert einer dieser Einstellungen ändern, müssen Sie die Versionsnummer erhöhen, indem Sie `setVersion()`. Die neuen Werte werden nur dann an den Client gesendet, wenn die Version auf dem Client älter als die aktuelle ist `ServerConfigData` -Version.

## Domänenübergreifende DRM-Richtliniendatei {#crossdomain-drm-policy-file}

Wenn der Lizenzserver auf einer anderen Domäne als der SWF gehostet wird, dann eine domänenübergreifende DRM-Richtliniendatei ( [!DNL crossdomain.xml]) erforderlich, damit die SWF Lizenzen von einem Lizenzserver anfordern kann. Eine domänenübergreifende DRM-Richtliniendatei wird durch eine XML-Datei dargestellt, mit der der Server angeben kann, dass seine Daten und Dokumente für SWF-Dateien verfügbar sind, die von anderen Domänen bereitgestellt werden. Jede SWF-Datei, die von einer Domäne bereitgestellt wird, die in der domänenübergreifenden DRM-Richtliniendatei des Lizenzservers angegeben ist, darf auf Daten oder Assets von diesem Lizenzserver zugreifen.

Adobe empfiehlt Entwicklern, bei der Bereitstellung der domänenübergreifenden Richtliniendatei die Best Practices zu befolgen, indem sie nur vertrauenswürdigen Domänen den Zugriff auf den Lizenzserver gewähren und den Zugriff auf den Lizenzunterordner auf dem Webserver beschränken.

Weitere Informationen zu domänenübergreifenden DRM-Richtliniendateien finden Sie unter den folgenden Speicherorten:

* Website-Steuerelemente (DRM-Richtliniendateien)
* Domänenübergreifende DRM-Richtliniendateispezifikation: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
