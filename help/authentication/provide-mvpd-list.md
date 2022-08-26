---
title: MVPD-Liste bereitstellen
description: MVPD-Liste bereitstellen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# MVPD-Liste bereitstellen {#provide-mvpd-list}

## REST-API-Endpunkte {#clientless-endpoints}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

&lt;reggie_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Produktion - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

 </br>

## Beschreibung {#description}

Gibt eine Liste der konfigurierten MVPDs für den Anfragenden zurück.

| Endpunkt | aufgerufen  </br>von | Eingabe   </br>Parameter | HTTP  </br>Methode | Reaktion | HTTP  </br>Reaktion |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/config/{requestorId}</br></br>Beispiel:</br></br>&lt;sp_fqdn>/api/v1/config/sampleRequestorId | Primetime-Authentifizierung | 1. Antragsteller</br>    (Pfadkomponente)</br>_2.  deviceType (nicht mehr unterstützt)_ | GET | XML oder JSON mit einer Liste von MVPDs. | 200 |

{style=&quot;table-layout:auto&quot;}


| Eingabeparameter | Beschreibung |
| --------------- | ------------------------------------------------------------- |
| Anforderer | Die Programmer-Anfrage-ID, für die dieser Vorgang gültig ist. |
| *deviceType* | Gerätetyp. |

{style=&quot;table-layout:auto&quot;}

### Beispielantwort {#sample-response}

Wie vorhandene MVPD-XML-Antwort auf /config-Servlet

Hinweis: Alle MVPDs, die für die Verwendung von Platform SSO konfiguriert sind, verfügen über die folgenden zusätzlichen Eigenschaften in ihrem entsprechenden Knoten (JSON/XML):

* **enablePlatformServices (boolean):** Markierung, die angibt, ob dieses MVPD über Platform SSO integriert wird
* **boardingStatus (Zeichenfolge):** Markierung, die angibt, ob der MVPD Platform SSO (SUPPORTED) vollständig unterstützt oder ob der MVPD nur in der Plattformauswahl (PICKER) angezeigt wird
* **displayInPlatformPicker (boolean):** sollte dieser MVPD in der Plattformauswahl angezeigt werden
* **platformMappingId (Zeichenfolge):** die Kennung dieses MVPD, wie von der Plattform bekannt
* **requiredMetadataFields (String-Array):** die Metadatenfelder des Benutzers, die bei erfolgreicher Anmeldung verfügbar sein sollen


[Zurück zur clientlosen API-Referenz](http://tve.helpdocsonline.com/clientless-api-reference)
