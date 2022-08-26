---
title: REST-API-Referenz
description: REST-API-Referenz
source-git-commit: 4c3a0dd56b4ef99ac8c57cfde61f792088b0ff4d
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 3%

---


# REST-API-Referenz {#rest-api-reference}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Antwortformate {#response-formats}


>[!NOTE]
>
> Die in diesen Diensten bereitgestellten APIs können Antworten in XML oder JSON zurückgeben (für APIs, die eine Antwort zurückgeben). Es gibt 3 verschiedene Möglichkeiten, das Antwortformat in der Anfrage anzugeben:
>* Setzen Sie HTTP Accept Header auf &quot;application/xml&quot;</code>&quot; oder &quot;application/json</code>&quot;
>* Geben Sie in der Anfrage-Payload den Parameter &quot;format=xml&quot;an</code>&quot; oder &quot;format=json</code>&quot;</li>
>* Rufen Sie den Webdienst-Endpunkt mit der Erweiterung .xml auf.</code> oder .json</code>. Beispiel: &quot;/regcode.xml</code>oder &quot;/regcode.json</code>&quot;
>
>Sie können eine der oben genannten Methoden angeben. Das Angeben mehrerer Methoden mit widersprüchlichen Formaten kann zu Fehlern oder unerwünschten Ausgaben führen.

## REST-API-Endpunkte {#clientless-endpoints}

&lt;reggie_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>


## Web Services - Zusammenfassung {#web_srvs_summary}

In der folgenden Tabelle sind die verfügbaren Webdienste für den clientlosen Ansatz aufgeführt. Klicken Sie auf die Webdienst-Endpunkte, um weitere Informationen zu erhalten (Beispielanfrage und -antwort, Eingabeparameter, HTTP-Methoden usw.).


| Sr | Web Service Endpoint | Beschreibung | [Diag.  </br>Ref](http://tve.helpdocsonline.com/api-reference-v2-test#illustration). | gehostet bei | aufgerufen von |
| --- | --- | --- | --- | --- | --- |
| 1. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode](http://tve.helpdocsonline.com/registration-code-request) | Gibt zufällig generierten Registrierungs-Code und Anmeldeseiten-URI zurück | 2 | Adobe  </br>Reg Code-Dienst | Smart Device |
| 2. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode/  </br>  {registrationCode}](http://tve.helpdocsonline.com/return-registration-record) | Gibt den Registrierungs-Code-Datensatz mit Registrierungs-Code-UUID, Registrierungs-Code und Hash-Geräte-ID zurück | 8 | Adobe  </br>Reg Code-Dienst | Primetime-Authentifizierung |
| 3. | [&lt;sp_fqdn>/api/v1/config/  </br>  {requestorId}](http://tve.helpdocsonline.com/provide-mvpd-list) | Gibt eine Liste der konfigurierten MVPDs für den Anforderer zurück | 5 | Adobe  </br>Primetime  </br>Authentifizierung  </br>Diensleistung | Anmelden  </br>Web  </br>App |
| 4. | [&lt;sp_fqdn>/api/v1/authenticate](http://tve.helpdocsonline.com/initiate-authentication) | Initiiert den AuthN-Prozess, indem das MVPD-Auswahlereignis informiert wird. Erstellt einen Datensatz in der Authentifizierungsdatenbank, der abgestimmt wird, wenn eine erfolgreiche Antwort von MVPD empfangen wird (Schritt 13) | 7 | Adobe  </br>Primetime  </br>Authentifizierung  </br>Diensleistung | Anmelden  </br>Web  </br>App |
| 5. | SAML Assertion Consumer | Vorhandener SAML-Workflow zwischen Primetime-Authentifizierung und MVPD | 13 | Primetime  </br>Authentifizierung  </br>Diensleistung | Primetime-Authentifizierung |
| 6. | [&lt;sp_fqdn>/api/v1/checkauthn/  </br>  {registrationCode}](http://tve.helpdocsonline.com/check-authentication-flow-by-second-screen-web-app) | Die Webanwendung &quot;Anmeldung&quot;kann prüfen, ob der versucht wurde, sich anzumelden |  | Primetime  </br>Authentifizierung   </br>Diensleistung | Anmelden   </br>Web   </br>App |
| 7. | [&lt;sp_fqdn>/api/v1/tokens/authn](http://tve.helpdocsonline.com/rest-api-retrieve-authentication-token) | Ruft AuthN-Token-bezogene Metadaten ab | 15 | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 8. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode/  </br>  {registrationCode}](http://tve.helpdocsonline.com/delete-registration-record) | Löscht den Reg-Codedatensatz und gibt den Reg-Code zur Wiederverwendung frei | 16 | Adobe  </br>Reg Code-Dienst | Primetime-Authentifizierung |
| 9. | [&lt;sp_fqdn>/api/v1/authorize](http://tve.helpdocsonline.com/initiate-authorization) | Erhält die Antwort auf die Autorisierung. | 17 | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 10. | [&lt;sp_fqdn>/api/v1/checkauthin](http://tve.helpdocsonline.com/check-authentication-token) | Gibt an, ob das Gerät über ein nicht abgelaufenes AuthN-Token verfügt. |  | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 11. | [&lt;sp_fqdn>/api/v1/tokens/authn](http://tve.helpdocsonline.com/rest-api-retrieve-authentication-token) | Gibt das AuthN-Token zurück, falls gefunden. |  | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 12. | [&lt;sp_fqdn>/api/v1/tokens/authz](http://tve.helpdocsonline.com/retrieve-authorization-token) | Gibt das AuthZ-Token zurück, falls gefunden. |  | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 13. | [&lt;sp_fqdn>/api/v1/tokens/media](http://tve.helpdocsonline.com/obtain-short-media-token) | Gibt das Short Media Token aus, falls vorhanden - identisch mit /api/v1/mediatoken |  | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 14. | [&lt;sp_fqdn>/api/v1/mediatoken](http://tve.helpdocsonline.com/obtain-short-media-token) | Erhält Short Media Token |  | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 15. | [&lt;sp_fqdn>/api/v1/preauthorize](http://tve.helpdocsonline.com/retrieve-list-of-preauthorized-resources) | Ruft die Liste der vorab autorisierten Ressource ab |  | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |
| 16. | [&lt;sp_fqdn>/api/v1/preauthorize/{code}](http://tve.helpdocsonline.com/retrieve-list-of-preauthorized-resources-by-way-of-web-app) | Ruft die Liste der vorab autorisierten Ressourcen ab |  | Primetime  </br>Authentifizierung  </br>Diensleistung | Webanwendung anmelden |
| 17. | [&lt;sp_fqdn>/api/v1/logout](http://tve.helpdocsonline.com/logout) | AuthN- und AuthZ-Token aus dem Speicher entfernen |  | Primetime  </br>Authentifizierung   </br>Diensleistung | Smart Device |
| 18. | [&lt;sp_fqdn>/api/v1/tokens/usermetadata](http://tve.helpdocsonline.com/user-metadata-call) | Ruft Benutzermetadaten nach Abschluss des Authentifizierungsflusses ab | Nicht zutreffend | Nicht zutreffend | Smart Device |
| 19. | [&lt;sp_fqdn>/api/v1/authenticate/freepreview](http://tve.helpdocsonline.com/free-preview-for-temp-pass-and-promotional-temp-pass) | Erstellen eines Authentifizierungstokens für den temporären Pass oder den temporären Weiterleitungs-Pass | Nicht zutreffend | Primetime  </br>Authentifizierung  </br>Diensleistung | Smart Device |

{style=&quot;table-layout:auto&quot;}

## REST API Security {#security}

Alle clientlosen Primetime-Authentifizierungs-APIs für die Authentifizierung müssen zur sicheren Kommunikation mithilfe des HTTPS-Protokolls aufgerufen werden. Darüber hinaus sollten die meisten APIs, die aufgerufen werden, ein Zugriffstoken enthalten, das von [Dynamische Kundenregistrierung](http://tve.helpdocsonline.com/dynamic-client-registration).


## Verwandte Informationen {#related}

* [REST API - Übersicht](http://tve.helpdocsonline.com/reset-api-overview)
* [Server-zu-Server-Cookbook](http://tve.helpdocsonline.com/server-to-server-cookbook)
* [Client-zu-Server-Cookbook](http://tve.helpdocsonline.com/client-to-server)
* [Vermeiden Sie die Verwendung von &quot;&amp;&#39;reg\_code&quot;in /authenticate request (Tech Note)](https://tve.zendesk.com/entries/23648011-Clientless-Avoid-using-reg-code-in-authenticate-request)
