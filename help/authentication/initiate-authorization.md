---
title: Autorisierung initiieren
description: Autorisierung initiieren
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# Autorisierung initiieren {#initiate-authorization}

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

Erhält die Antwort auf die Autorisierung. 

| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/authorize | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. Antragsteller (erforderlich)</br>2.  deviceId (Obligatorisch)</br>3.  resource (erforderlich)</br>4.  device_info/X-Device-Info (erforderlich)</br>5.  _deviceType_</br> 6.  _deviceUser_ (Veraltet)</br>7.  _appId_ (Veraltet)</br>8.  Zusätzliche Parameter (optional) | GET | XML oder JSON mit Autorisierungsdetails oder Fehlerdetails, falls nicht erfolgreich. Siehe Beispiele unten. | 200 - Erfolg  </br>403 - Kein Erfolg |

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
| zusätzliche Parameter | Der Aufruf kann auch optionale Parameter enthalten, die andere Funktionen wie:</br></br>* generic_data - ermöglicht die Verwendung von [Promotional TempPass](https://tve.helpdocsonline.com/promotional-temp-pass)</br></br>Beispiel: `generic_data=("email":"email@domain.com")` |

{style=&quot;table-layout:auto&quot;}

>[!CAUTION]
>
>**IP-Adresse des Streaming-Geräts**</br>
>Bei Client-zu-Server-Implementierungen wird die IP-Adresse des Streaming-Geräts implizit mit diesem Aufruf gesendet.  Bei Server-zu-Server-Implementierungen, bei denen die Variable **regcode** wird vom Programmierer-Dienst und nicht vom Streaming-Gerät aufgerufen. Der folgende Header ist erforderlich, um die IP-Adresse des Streaming-Geräts zu übergeben:</br></br>
>
>
```
>X-Forwarded-For : <streaming\_device\_ip>
>```
>
>where `<streaming\_device\_ip>` ist die öffentliche IP-Adresse des Streaming-Geräts.</br></br>
>Beispiel :</br>
>
>
```
>POST /reggie/v1/{req_id}/regcode HTTP/1.1
>X-Forwarded-For:203.45.101.20
>```


### Beispielantwort {#sample-response}

* **1. Fall: Erfolg**

</br>
  * **XML:**
  </br>
    ```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <authorization>
    <expires>1348148289000</expires>
    <mvpd>sampleMvpdId</mvpd>
    <requestor>sampleRequestorId</requestor>
    <resource>sampleResourceId</resource>
    </authorization>
    ```



* **JSON:**

   ```JSON
   {
     "mvpd": "sampleMvpdId",
     "resource": "sampleResourceId",
     "requestor": "sampleRequestorId",
     "expires": "1348148289000"
   }
   ```

>[!IMPORTANT]
>
>Wenn die Antwort von einem Proxy-MVPD stammt, kann sie ein zusätzliches Element namens `proxyMvpd`. 

 

* **2. Fall: Genehmigung verweigert**


   ```JSON
   <error>
     <status>403</status>
     <message>User not authorized</message>
     <details>Your subscription package does not include the "ASFAFD" channel.
     Please go to http://www.ca.ble/upgrade in order to upgrade your subscription.</details>
   </error>
   ```

[Zurück zur REST-API-Referenz](http://tve.helpdocsonline.com/rest-api-reference)
