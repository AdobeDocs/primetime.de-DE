---
title: Authentifizierungstoken abrufen
description: Authentifizierungstoken abrufen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Authentifizierungstoken abrufen {#retrieve-authentication-token}

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

Ruft Authentifizierungs-Token (AuthN) ab.  

| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/authn</br></br>Beispiel:</br></br>&lt;sp_fqdn>/api/v1/tokens/authn | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. Antragsteller (erforderlich)</br>2.  deviceId (Obligatorisch)</br>3.  device_info/X-Device-Info (erforderlich)</br>4.  _deviceType_ (Veraltet)</br>5.  _deviceUser_ (Veraltet)</br>6.  _appId_ (Veraltet) | GET | XML oder JSON mit Authentifizierungsinformationen oder Fehlerdetails, falls nicht erfolgreich. | 200 - Erfolg.  </br>404 - Token nicht gefunden  </br>410 - Token abgelaufen |

{style=&quot;table-layout:auto&quot;}


| Eingabeparameter | Beschreibung |
| --- | --- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| deviceId | Die Geräte-ID-Bytes. |
| device_info/</br></br>X-Device-Info | Informationen zum Streaming-Gerät.</br></br>**Hinweis**: Dieser Parameter kann als URL-Parameter an device_info übergeben werden. Aufgrund der potenziellen Größe dieses Parameters und der Längenbeschränkungen einer GET-URL sollte er jedoch als X-Device-Info in der HTTP-Kopfzeile übergeben werden. </br></br>Weitere Informationen finden Sie unter [Weitergeben von Geräte- und Verbindungsinformationen](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Der Gerätetyp (z. B. Roku, PC).</br></br>**Hinweis**: ersetzt device_info diesen Parameter. |
| _deviceUser_ | Die Benutzer-ID des Geräts.</br></br>**Hinweis**: Bei Verwendung von sollte deviceUser dieselben Werte wie im [Registrierungscode erstellen](http://tve.helpdocsonline.com/registration-code-request) -Anfrage. |
| _appId_ | Die Anwendungs-ID/der Name. </br></br>**Hinweis**: ersetzt device_info diesen Parameter. Falls verwendet, `appId` sollte dieselben Werte wie im [Registrierungscode erstellen](http://tve.helpdocsonline.com/registration-code-request) -Anfrage. |

{style=&quot;table-layout:auto&quot;}

</br>

### Beispielantwort {#response}

 

#### Erfolg

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <authentication>
         <expires>1601114932000</expires>
         <userId>sampleUserId</userId>
         <mvpd>sampleMvpdId</mvpd>
         <requestor>sampleRequestor</requestor>
    </authentication>
```


**JSON:**

```JSON
    {
         "requestor": "sampleRequestor",
         "mvpd": "sampleMvpdId",
         "userId": "sampleUserId",
         "expires": "1601114932000"
    }
```

 

 

#### Authentifizierungstoken nicht gefunden:

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <error>
        <status>404</status>
        <message>Not found</message>
    </error>
```

 
**JSON:**

```JSON
    {
        "status": 404,
        "message": "Not Found"
    }
```

[Zurück zur clientlosen API-Referenz](http://tve.helpdocsonline.com/clientless-api-reference)
