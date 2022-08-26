---
title: Autorisierungstoken abrufen
description: Autorisierungstoken abrufen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# Autorisierungstoken abrufen {#retrieve-authorization-token}

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

Ruft Autorisierungs-Token (AuthZ) ab.  


| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/authz</br></br>Beispiel:</br></br>&lt;sp_fqdn>/api/v1/tokens/authz | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. Antragsteller (erforderlich)</br>2.  deviceId (Obligatorisch)</br>3.  resource (erforderlich)</br>4.  device_info/X-Device-Info (erforderlich)</br>5.  _deviceType_</br> 6.  _deviceUser_ (Veraltet)</br>7.  _appId_ (Veraltet) | GET | 1. Erfolg</br>2.  Authentifizierungstoken  </br>    nicht gefunden oder abgelaufen:   </br>    XML erklärt Grund  </br>    für Autoren-Token nicht gefunden</br>3.  Autorisierungstoken  </br>    nicht gefunden:  </br>    XML-Erklärung</br>4.  Autorisierungstoken  </br>    abgelaufen:  </br>    XML-Erklärung | 200 - Erfolg  </br>412 - Keine AuthN</br></br>404 - No AuthZ</br></br>410 - AuthZ abgelaufen |

{style=&quot;table-layout:auto&quot;}

</br>

| Eingabeparameter | Beschreibung |
| --- | --- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| deviceId | Die Geräte-ID-Bytes. |
| resource | Eine Zeichenfolge, die eine resourceId (oder ein MRSS-Fragment) enthält, den von einem Benutzer angeforderten Inhalt identifiziert und von MVPD-Autorisierungsendpunkten erkannt wird. |
| device_info/</br></br>X-Device-Info | Informationen zum Streaming-Gerät.</br></br>**Hinweis**: Dieser Parameter kann als URL-Parameter an device_info übergeben werden. Aufgrund der potenziellen Größe dieses Parameters und der Längenbeschränkungen einer GET-URL sollte er jedoch als X-Device-Info in der HTTP-Kopfzeile übergeben werden. </br></br>Weitere Informationen finden Sie unter [Weitergeben von Geräte- und Verbindungsinformationen](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Der Gerätetyp (z. B. Roku, PC).</br></br>Wenn dieser Parameter korrekt festgelegt ist, bietet ESM Metriken an, die [aufgeschlüsselt nach Gerätetyp](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) bei Verwendung von ClientLess, sodass verschiedene Arten der Analyse für z. B. Roku, AppleTV, Xbox usw. durchgeführt werden können.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**Hinweis**: ersetzt device_info diesen Parameter. |
| _deviceUser_ | Die Benutzer-ID des Geräts. |
| _appId_ | Die Anwendungs-ID/der Name. </br></br>**Hinweis**: ersetzt device_info diesen Parameter. |

{style=&quot;table-layout:auto&quot;}


### Beispielantwort {#response}

 

#### Erfolg

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <authorization>
        <expires>1348148289000</expires>
        <mvpd>sampleMvpdId</mvpd>
        <requestor>sampleRequestorId</requestor>
        <resource>sampleResourceId</resource>
        <proxyMvpd>sampleProxyMvpdId</proxyMvpd>
    </authorization>
```

 

**JSON:**

```JSON
    {
        "mvpd": "sampleMvpdId",
        "resource": "sampleResourceId",
        "requestor": "sampleRequestorId",
        "expires": "1348148289000",
        "proxyMvpd": "sampleProxyMvpdId"
    }
```

 </br>


#### Authentifizierungstoken nicht gefunden oder abgelaufen:

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <error>
        <status>412</status>
        <message>User not authenticated</message>
    </error>
```

 

**JSON:**

```JSON
    {
        "status": 412,
        "message": "User not authenticated",
        "details": null
    }
```

</br>
 

#### Autorisierungstoken nicht gefunden:

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
        "message": "Not Found",
        "details": null
    }
```

</br>

 

#### Autorisierungstoken abgelaufen:

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <error>
        <status>410</status>
        <message>Gone</message>
    </error>
```

 

**JSON:**

```JSON
    {
        "status": 410,
        "message": "Gone",
        "details": null
    }
```

[Zurück zur clientlosen API-Referenz](http://tve.helpdocsonline.com/clientless-api-reference)
