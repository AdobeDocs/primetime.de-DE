---
title: REST API-Cookbook (Client-to-Server)
description: REST API-Cookbook-Client zu Server.
source-git-commit: 4c3a0dd56b4ef99ac8c57cfde61f792088b0ff4d
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 1%

---


# REST API-Cookbook (Client-to-Server) {#rest-api-cookbook-client-to-server}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.


## Übersicht {#overview}

Dieses Dokument enthält eine schrittweise Anleitung für das Entwicklungsteam eines Programmierers zur Integration eines &quot;intelligenten Geräts&quot;(Spielkonsole, Smart TV-App, Set-Top-Box usw.) mit Adobe Primetime-Authentifizierung mithilfe von REST-API-Diensten. Dieser Client-zu-Server-Ansatz, der REST-APIs anstelle eines Client-SDK verwendet, ermöglicht eine breitere Unterstützung verschiedener Plattformen, für die die Entwicklung einer beträchtlichen Anzahl eindeutiger SDKs nicht möglich wäre. Einen umfassenden technischen Überblick über die Funktionsweise der Clientless-Lösung finden Sie im Abschnitt [Clientlose technische Übersicht](/help/authentication/rest-api-overview.md).


Für diesen Ansatz sind zwei Komponenten erforderlich (Streaming-App und AuthN-App), um die erforderlichen Flüsse abzuschließen: Start-, Registrierungs-, Autorisierungs- und View-Media-Flüsse in der Streaming-App und der Authentifizierungsfluss in Ihrer AuthN-App.

## Komponenten {#components}

In einer funktionierenden Client-zu-Server-Lösung sind die folgenden Komponenten involviert:

 

| Typ | Komponente | Beschreibung |
| --- | --- | --- |
| Streaming-Gerät | Streaming-App | Die Programmeranwendung, die sich auf dem Streaming-Gerät des Benutzers befindet und authentifizierte Videos wiedergibt. |
|  | \[Optional\] AuthN-Modul | Wenn das Streaming-Gerät über einen Benutzeragenten (d. h. einen Webbrowser) verfügt, ist das AuthN-Modul für die Authentifizierung des Benutzers auf dem MVPD IdP verantwortlich. |
| \[Optional\] AuthN-Gerät | AuthN App | Wenn das Streaming-Gerät über keinen Benutzeragenten (d. h. einen Webbrowser) verfügt, ist die AuthN-Anwendung eine Programmierer-Webanwendung, auf die über einen Webbrowser von einem Gerät eines anderen Benutzers aus zugegriffen wird.  |
| Adobe | Adobe Pass-Dienst | Ein Dienst, der mit dem MVPD IdP- und AuthZ-Dienst integriert wird und Authentifizierungs- und Autorisierungsentscheidungen ermöglicht. |
| MVPD-Infrastruktur | MVPD IdP | Ein MVPD-Endpunkt, der einen auf Anmeldedaten basierenden Authentifizierungsdienst bereitstellt, um die Identität des Benutzers zu überprüfen. |
|  | MVPD AuthZ-Dienst | Ein MVPD-Endpunkt, der Autorisierungsentscheidungen basierend auf den Abonnements des Benutzers, elterlichen Kontrollen usw. bereitstellt. |

 

Weitere im Fluss verwendete Begriffe werden im Abschnitt [Glossar](http://tve.helpdocsonline.com/adobe-pass-glossary).

## Flüsse{#flows}

### Dynamische Kundenregistrierung (DCR)

Adobe Pass verwendet DCR, um die Client-Kommunikation zwischen einer Programmieranwendung oder einem Server und den Adobe Pass-Diensten zu sichern. Der DCR-Fluss ist ein separater, abhängiger und erforderlicher Fluss und kann hier gefunden werden: http://tve.helpdocsonline.com/dynamic-client-registration


### App-Flüsse für Streaming (Smart Device)

![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/clientless_1st_screen_updated.PNG)

 

#### Startup-Fluss

1. Ihre App wird gestartet und lädt die ursprüngliche Benutzeroberfläche.

2. Abrufen/Generieren einer Geräte-ID.

3. Führen Sie einen Check-Authentication-Aufruf aus, um zu sehen, ob das Gerät bereits authentifiziert ist.  Beispiel: [`<SP_FQDN>/api/v1/checkauthn [device ID]`](/help/authentication/check-authentication-token.md)

4. Wenn die Variable `checkauthn` -Aufruf erfolgreich ausgeführt wurde, fahren Sie ab Schritt 2 mit dem Autorisierungsfluss fort.  Wenn dies fehlschlägt, starten Sie den Registrierungsablauf.

 

#### Registrierungsfluss

1. Rufen Sie einen Registrierungs-Code und eine URL ab, die Ihr Benutzer für den Zugriff auf Ihre Anmeldung auf dem 2. Bildschirm verwenden kann, und stellen Sie diese dem Benutzer vor:

   a. Senden Sie eine POST-Anfrage an den Adobe Registration Code-Dienst und übergeben Sie eine Hash-Geräte-ID und eine &quot;Registrierungs-URL&quot;.  Beispiel: [`<REGGIE_FQDN>/reggie/v1/[requestorId]/regcode [device ID]`](/help/authentication/registration-code-request.md)

   b. Präsentieren Sie dem Benutzer den zurückgegebenen Registrierungs-Code und die URL.

   c. Weisen Sie den Benutzer an, zu einem Web-fähigen Gerät zu wechseln, navigieren Sie zur URL und geben Sie dann den Registrierungs-Code ein.

 

#### Autorisierungsfluss

1. Der Benutzer kehrt von der zweiten Bildschirmanwendung zurück und drückt auf dem Gerät die Schaltfläche &quot;Weiter&quot;. Alternativ können Sie einen Abruffegel implementieren, um den Authentifizierungsstatus zu überprüfen. Die Adobe Primetime-Authentifizierung empfiehlt jedoch die Methode für die Schaltfläche &quot;Fortfahren&quot;vor der Abfrage. <!--(For information on employing a "Continue" button versus polling the Adobe Primetime authentication backend server, see the Clientless Technical Overview: Managing 2nd-Screen Workflow Transition.)--> Beispiel: [\&lt;sp _fqdn=&quot;&quot;>/api/v1/tokens/authn](/help/authentication/retrieve-authentication-token.md)

2. Senden Sie eine GET-Anfrage an den Adobe Primetime-Authentifizierungsdienst, um die Autorisierung zu initiieren. Beispiel: `<SP_FQDN>/api/v1/authorize [device ID, Requestor ID, Resource ID]`

<!-- end list -->

- Wenn die Antwort den Erfolg anzeigt: Der Benutzer verfügt über ein gültiges AuthN-Token UND der Benutzer ist berechtigt, das angeforderte Medium zu sehen (für diesen Benutzer gibt es ein gültiges AuthZ-Token).

- Wenn die Antwort auf einen Fehler hinweist: Überprüfen Sie die ausgelöste Ausnahme, um ihren Typ zu ermitteln (AuthN, AuthZ oder etwas Anderes):

   - Wenn es sich um einen AuthN-Fehler handelt, starten Sie den Registrierungs-Fluss neu.

   - Wenn es sich um einen AuthZ-Fehler handelt, ist der Benutzer nicht berechtigt, das angeforderte Medium anzuzeigen, und dem Benutzer sollte eine Fehlermeldung angezeigt werden.

   - Wenn ein anderer Fehler aufgetreten ist (Verbindungsfehler, Netzwerkfehler usw.) zeigen Sie dem Benutzer eine entsprechende Fehlermeldung an.

 

#### Medienfluss anzeigen

1. Aktuelle Medienoptionen. Der Benutzer wählt das Medium aus, das angezeigt werden soll.

2. Sind die Medien geschützt?

   a. Ihre App prüft, ob die Medien geschützt sind.

   b. Wenn das Medium geschützt ist, startet Ihre App den obigen Autorisierungsfluss (AuthZ).

   c. Wenn das Medium nicht geschützt ist, können Sie das Medium für den Benutzer wiedergeben.

3. Wiedergabe des Mediums.


### AuthN (2. Bildschirm) App-Fluss

![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/smart_dev_second_flow.png)

1. Rufen Sie eine Liste der MVPDs für diesen Benutzer ab. Beispiel: [`<SP_FQDN>/api/v1/config/[requestorID]`](/help/authentication/provide-mvpd-list.md)

1. Starten Sie den Authentifizierungsfluss.  Beispiel: [`<SP_FQDN>/api/v1/authenticate [requestorID, MVPD ID, Redirect URL, Domain name, Registration Code, "noflash=true"]`](/help/authentication/initiate-authentication.md)

1. Überprüfen Sie, ob die Authentifizierung erfolgreich war.  Beispiel: [`<SP_FQDN>/api/v1/checkauthn/[registration code][requestor ID]`](/help/authentication/check-authentication-token.md)

1. Senden Sie den Benutzer zurück an Ihre Smart-Device-App, um den Autorisierungsfluss abzuschließen.

 

## Platform SSO {#platform-sso}

Einige Plattformen bieten dedizierte Unterstützung für Single Sign-On (SSO). Implementierungsdetails finden Sie für jede Plattform:

- [Apple SSO](http://tve.helpdocsonline.com/rest-api-apple-sso)
- Amazon SSO

## TempPass und Promotional TempPass für REST-API {#temppass}

Bei TempPass - und Promotional TempPass -Implementierungen, bei denen der Benutzer keine Anmeldeinformationen eingeben muss, kann die Authentifizierung direkt in der Streaming-App implementiert werden. 

**Um diese API verwenden zu können, muss die Streaming-App sicherstellen, dass die Geräte-ID eindeutig ist, da sie zur Identifizierung des Tokens verwendet wird, sowie die optionalen zusätzlichen Daten.**


![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/Free%20preview%20option.png?dc=201612071020-0)

### Verwandte Informationen {#related}

- [REST-API-Referenz](/help/authentication/rest-api-reference.md)
