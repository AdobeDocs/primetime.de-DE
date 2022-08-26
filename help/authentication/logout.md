---
title: Initiate Logout
description: Abmeldung starten
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# Initiate Logout {#initiate-logout}

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

Entfernen Sie AuthN- und AuthZ-Token aus dem Speicher.


| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/logout | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. Anforderer</br>2.  deviceId (Obligatorisch)</br>3.  device_info/X-Device-Info (erforderlich)</br>4.  _deviceType_</br> 5.  _deviceUser_ (Veraltet)</br>6.  _appId_ (Veraltet) | DELETE | Keines | 204 |


| Eingabeparameter | Beschreibung |
| --- | --- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| deviceId | Die Geräte-ID-Bytes. |
| device_info/</br></br>X-Device-Info | Informationen zum Streaming-Gerät.</br></br>**Hinweis**: Dieser Parameter kann als URL-Parameter an device_info übergeben werden. Aufgrund der potenziellen Größe dieses Parameters und der Längenbeschränkungen einer GET-URL sollte er jedoch als X-Device-Info in der HTTP-Kopfzeile übergeben werden. </br></br>Weitere Informationen finden Sie unter [Weitergeben von Geräte- und Verbindungsinformationen](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Der Gerätetyp (z. B. Roku, PC).</br></br>Wenn dieser Parameter korrekt festgelegt ist, bietet ESM Metriken an, die [aufgeschlüsselt nach Gerätetyp](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) bei Verwendung von ClientLess, sodass verschiedene Arten der Analyse für z. B. Roku, AppleTV, Xbox usw. durchgeführt werden können.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**Hinweis**: ersetzt device_info diesen Parameter. |
| _deviceUser_ | Die Benutzer-ID des Geräts.</br></br>**Hinweis**: Bei Verwendung von sollte deviceUser dieselben Werte wie im [Registrierungscode erstellen](http://tve.helpdocsonline.com/registration-code-request) -Anfrage. |
| _appId_ | Die Anwendungs-ID/der Name. </br></br>**Hinweis**: ersetzt device_info diesen Parameter. Falls verwendet, `appId` sollte dieselben Werte wie im [Registrierungscode erstellen](http://tve.helpdocsonline.com/create-registration-page-/-login-uri) -Anfrage. |

>[!IMPORTANT]
> 
>Der Abmelde-Aufruf hat derzeit die folgende Einschränkung: es löscht die AuthN- und AuthZ-Token aus dem Speicher (d. h. auf der Authentifizierungsseite von Programmierer/Primetime), aber **nicht** Rufen Sie den MVPD-Abmelde-Endpunkt auf. 

### [Zurück zur REST-API-Referenz](/help/authentication/rest-api-reference.md)
