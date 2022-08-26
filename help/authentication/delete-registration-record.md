---
title: Registrierungsdatensatz löschen
description: Registrierungsauflistung löschen
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Registrierungsdatensatz löschen {#delete-registration-record}

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


## Beschreibung {#delete-record}

Löscht den reg-Code-Datensatz und gibt den reg-Code zur Wiederverwendung frei. 

| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;reggie_fqdn>/reggie/v1/{requestorId}/regcode/{registrationCode}</br></br>Beispiel:</br></br>&lt;reggie_fqdn>/reggie/v1/regcode/ER45RTY | Streaming-App</br></br>oder</br></br>Programmiererdienst | 1. Anforderer-ID  </br>    (Pfadkomponente)</br>2.  Registrierungs-Code  </br>    (Pfadkomponente) | DELETE | Keines | 204 |

{style=&quot;table-layout:auto&quot;}

</br>

| Eingabeparameter | Beschreibung |
| --- | --- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| Registrierungscode | Der Registrierungscode-Wert, der auf dem Streaming-Gerät angezeigt wird (in den Authentifizierungsfluss einzugeben). |

{style=&quot;table-layout:auto&quot;}

</br>

### [Zurück zur REST-API-Referenz](http://tve.helpdocsonline.com/rest-api-reference)
