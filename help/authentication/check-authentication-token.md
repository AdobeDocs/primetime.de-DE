---
title: Authentifizierungstoken überprüfen
description: Authentifizierungstoken überprüfen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Authentifizierungstoken überprüfen {#check-authentication-token}

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

Gibt an, ob das Gerät über ein nicht abgelaufenes Authentifizierungstoken verfügt.

| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/checkauthin | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. Antragsteller (erforderlich)</br>2.  deviceId (Obligatorisch)</br>3.  device_info/X-Device-Info (erforderlich)</br>4.  _deviceType_ </br>5.  _deviceUser_ (Veraltet)</br>6.  _appId_ (Veraltet) | GET | XML oder JSON mit Fehlerdetails, falls nicht erfolgreich. | 200 - Erfolg   </br>403 - Kein Erfolg |

{style=&quot;table-layout:auto&quot;}


| Eingabeparameter | Beschreibung |
| --- | --- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| deviceId | Die Geräte-ID-Bytes. |
| device_info/</br></br>X-Device-Info | Informationen zum Streaming-Gerät.</br></br>**Hinweis**: Dieser Parameter kann als URL-Parameter an device_info übergeben werden. Aufgrund der potenziellen Größe dieses Parameters und der Längenbeschränkungen einer GET-URL sollte er jedoch als X-Device-Info in der HTTP-Kopfzeile übergeben werden. </br></br>Weitere Informationen finden Sie unter [Weitergeben von Geräte- und Verbindungsinformationen](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Der Gerätetyp (z. B. Roku, PC).</br></br>Wenn dieser Parameter korrekt festgelegt ist, bietet ESM Metriken an, die [aufgeschlüsselt nach Gerätetyp](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) bei Verwendung von ClientLess, sodass verschiedene Arten der Analyse für z. B. Roku, AppleTV, Xbox usw. durchgeführt werden können.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br>**Hinweis**: ersetzt device_info diesen Parameter. |
| _deviceUser_ | Die Benutzer-ID des Geräts. |
| _appId_ | Die Anwendungs-ID/der Name.</br>**Hinweis**: ersetzt device_info diesen Parameter. |

{style=&quot;table-layout:auto&quot;}


## Antwort (falls nicht erfolgreich) {#response}

```JSON
    <error>
      <status>403</status>
      <message>Authentication token expired</message>
    </error>
```

### [Zurück zur REST-API-Referenz](http://tve.helpdocsonline.com/rest-api-reference)
