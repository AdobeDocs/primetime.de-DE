---
title: Platform SSO-Token für Adobe-Token austauschen
description: Platform SSO-Token für Adobe-Token austauschen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 2%

---


# Platform SSO-Token für Adobe-Token austauschen {#exchange-a-platform-sso-token-for-an-adobe-token}

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

Ermöglicht den &quot;Austausch&quot;eines Platform-SSO-Profils durch ein Adobe-Token.

| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/authn | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. Antragsteller (erforderlich)</br>    </br>2.  deviceId (Obligatorisch)</br>    </br>3.  mvpd (erforderlich)</br>    </br>4.  deviceType (Obligatorisch)</br>    </br>5.  SAMLResponse (erforderlich)</br>    </br>6.  deviceUser (nicht mehr unterstützt)</br>    </br>7.  appId (nicht mehr unterstützt) | POST | Die erfolgreiche Antwort lautet &quot;No Content&quot;(Kein Inhalt) 204 und gibt an, dass das Token erfolgreich erstellt wurde und für die Authoring-Flüsse verwendet werden kann. | 204 - Kein Inhalt   </br>400 - Ungültige Anfrage |


| Eingabeparameter | Beschreibung |
| --- | --- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| deviceId | Die Geräte-ID-Bytes. |
| mvpd | Die MVPD-ID, für die dieser Vorgang gültig ist. |
| deviceType | Die Apple-Plattform, für die wir versuchen, eine Profilanfrage zu erhalten.  Entweder **iOS** oder **tvOS**. |
| SAMLResponse | Das von Platform SSO zurückgegebene tatsächliche Profil. |
| _deviceUser_ | Die Benutzer-ID des Geräts. |
| _appId_ | Die Anwendungs-ID/der Name. |



### [Zurück zur REST-API-Referenz](http://tve.helpdocsonline.com/rest-api-reference)
