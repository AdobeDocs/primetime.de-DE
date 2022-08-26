---
title: Profil-Anfrage für Platform SSO abrufen
description: Profil-Anfrage für Platform SSO abrufen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Profil-Anfrage für Platform SSO abrufen {#retrieve-platform-sso-profile-request}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## REST-API-Endpunkte {#clientless-endpoints}

&lt;reggie_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>

## Beschreibung {#description}

Diese Ressource erzeugt Profilanfragen für eine Anforderungs-ID und einen MVPD-Tupel.


| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/{requestor}/profile-requests/{mvpd} | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. requestor (path param)</br>2. mvpd (path param)</br>3. deviceType (Obligatorisch) | GET | Der Content-Type der Antwort ist application/octet-stream, da die tatsächliche Payload für die Client-Anwendung undurchsichtig ist.</br></br>Die Antwort sollte von der Anwendung an die Plattform weitergeleitet werden</br></br>SSO-Engine zum Abrufen einer Profil-SSO. | 200 - Erfolg   </br>400 - Ungültige Anfrage |


| Eingabeparameter | Beschreibung |
| --------------- | -------------------------------------------------------------------------------------------------------- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| mvpd | Die MVPD-ID, für die dieser Vorgang gültig ist. |
| deviceType | Die Apple-Plattform, für die wir versuchen, eine Profilanfrage zu erhalten.  Entweder **iOS** oder **tvOS**. |

### [Zurück zur REST-API-Referenz](http://tve.helpdocsonline.com/rest-api-reference)
