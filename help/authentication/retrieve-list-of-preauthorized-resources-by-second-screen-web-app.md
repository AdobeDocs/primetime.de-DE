---
title: Abrufen einer Liste vorab autorisierter Ressourcen von der Second Screen Web App
description: Abrufen einer Liste vorab autorisierter Ressourcen von der Second Screen Web App
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Abrufen einer Liste vorab autorisierter Ressourcen von der Second Screen Web App {#retrieve-list-of-preauthorized-resources-by-second-screen-web-app}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## REST-API-Endpunkte {#clientless-endpoints}

&lt;reggie_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>

## Beschreibung {#description}

Anfrage an die Adobe Primetime-Authentifizierung zum Abrufen der Liste der vorautorisierten Ressourcen.

Es gibt zwei Gruppen von APIs: einen Satz für die Streaming-App oder den Programmierer-Dienst und einen Satz für die Second Screen Web App. Auf dieser Seite wird die API für die AuthN-App beschrieben.


| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/preauthorize/{Registrierungs-Code} | AuthN-Modul | 1. Registrierungs-Code  </br>    (Pfadkomponente)</br>2.  Antragsteller (erforderlich)</br>3.  Ressourcenliste (erforderlich) | GET | XML oder JSON, die einzelne Entscheidungen vor der Autorisierung oder Fehlerdetails enthalten. Siehe Beispiele unten. | 200 - Erfolg</br></br>400 - Ungültige Anfrage</br></br>401 - Unerlaubt</br></br>405 - Methode nicht zulässig  </br></br>412 - Vorbedingung fehlgeschlagen</br></br>500 - Interner Server-Fehler |



| Eingabeparameter | Beschreibung |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Registrierungscode | Der vom Benutzer am Anfang des Authentifizierungsflusses angegebene Registrierungscode-Wert. |
| Anfragender | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| Ressourcenliste | Eine Zeichenfolge, die eine kommagetrennte Liste von resourceIds enthält, die den Inhalt identifiziert, auf den ein Benutzer zugreifen kann, und die von MVPD-Autorisierungsendpunkten erkannt wird. |


### Beispielantwort {#sample-response}

**XML:**

```XML
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4`
Adobe-Response-Confidence : full
Content-Type: application/xml; charset=utf-8

<resources>
    <resource>
        <id>TestStream1</id>
        <authorized>true</authorized>
    </resource>
    <resource>
        <id>TestStream2</id>
        <authorized>false</authorized>  
        <error>
            <status>403</status>
            <code>authorization_denied_by_mvpd</code>
            <message>User not authorized</message>
            <details>Your subscription package does not include the "TestStream3" channel.</details>
            <helpUrl>https://experienceleague-review.corp.adobe.com/docs/primetime/authentication/auth-features/error-reportn/enhanced-error-codes.html#error-codes</helpUrl>
            <trace>0453f8c8-167a-4429-8784-cd32cfeaee58</trace>
            <action>none</action>
        </error>
    <resource>
</resources>
```

**JSON:**

```JSON
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4
Adobe-Response-Confidence : full
Content-Type: application/json; charset=utf-8
 
{
   "resources" : [
        {
            "id" : "TestStream1",
            "authorized" : true
        },
        {
            "id" : "TestStream3",
            "authorized" : false,
            "error" : {
               "status" : 403,
               "code" : "authorization_denied_by_mvpd",
               "message" : "User not authorized",
               "details" : "Your subscription package does not include the "TestStream3" channel.",
               "helpUrl" : "https://experienceleague-review.corp.adobe.com/docs/primetime/authentication/auth-features/error-reportn/enhanced-error-codes.html#error-codes",
               "trace" : "0453f8c8-167a-4429-8784-cd32cfeaee58",
               "action" : "none"
            }
        } 
    ]
}
```
