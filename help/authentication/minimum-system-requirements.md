---
title: Mindestsystemanforderungen
description: Mindestsystemanforderungen
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Mindestsystemanforderungen {#minimum-system-requirements}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.


## Übersicht {#overview}

In diesem Dokument werden die aktuellen Software- und Hardwareanforderungen für die Implementierung von Adobe Primetime-Authentifizierungsintegrationen auf unterstützten Plattformen beschrieben. Alle unten aufgeführten unterstützten Web-/Mobilbrowser und Betriebssysteme werden vom Adobe Primetime-Authentifizierungsteam vollständig unterstützt, das an die vereinbarten SLAs gebunden ist.

Als Adobe Primetime-Authentifizierungsteam fördern wir die Verwendung der neuesten stabilen Versionen der Browser und Betriebssysteme. Wir erkennen auch das Vorhandensein von inkompatiblen/älteren Plattformen und Browsern an, die derzeit verwendet werden. Diese veralteten Geräte funktionieren möglicherweise weiterhin problemlos, sind jedoch fehleranfälliger.

Der anfängliche Ansatz, Probleme zu beheben, die auf diesen veralteten Plattformen auftreten, sollte ein Upgrade auf die neuesten Versionen sein. Dabei kann es sich um die Betriebssystemversion, die Browserversion oder die Version der installierten Anwendung handeln.

Alle Probleme, die auf diesen Plattformen auftreten, werden vom Adobe Primetime-Authentifizierungsteam nach besten Kräften behoben. 

Adobe Primetime ermutigt unsere Kunden und Partner, ein Upgrade auf die neuesten Versionen in Erwägung zu ziehen, um neben der Verbesserung der Leistung, Effizienz und Sicherheit auch die volle Unterstützung der Adobe bei potenziellen Problemen zu erhalten. 


## Browser- und Betriebssystemanforderungen {#browser-OS-system-requirements}


| Web-/Mobilbrowser (†) | Unterstützte Versionen |
|---|---|
| Google Chrome | **70** oder höher |
| Mozilla Firefox | **57** oder höher |
| Apple Safari | **14** oder höher |
| Microsoft Edge | **100** oder höher |

(†) Adobe rät von der Verwendung des privaten oder Inkognito-Modus ab.

| Betriebssystem | Unterstützte Versionen |
|---|---|
| *Android* | **7,0** (Nougat) oder höher |
| *iOS* | **14** oder höher |
| *iPadOS* | **14** oder höher |
| *tvOS* | **14** oder höher |
| *Fire OS* | **5 (Android 5.1)** oder höher |
| *Mac OS* | **10,13** oder höher |
| *Microsoft Windows* | **10** oder höher |




>[!NOTE]
>
>Drittanbieter-Cookies - Berechtigungsflüsse zur Adobe Primetime-Authentifizierung schlagen möglicherweise fehl, wenn Drittanbieter-Cookies deaktiviert sind.  Dieses Problem tritt nur bei Änderung der Browsereinstellungen auf. Bei allen unterstützten Browsern sollte die Primetime-Authentifizierung mit den Standardeinstellungen funktionieren.\
 

## Geräteanforderungen für clientlose (REST)-Implementierungen {#general_clientless_reqs}

 
Jedes Gerät, das Adobe Primetime-Authentifizierungsdienste über clientlose Implementierungen nutzt **muss**:

* Stellen Sie eine eindeutige Hash-Geräte-ID bereit. Wenn das Gerät keine eindeutige Hash-Geräte-ID bereitstellt, muss es in der Lage sein, eine eindeutige ID beizubehalten, die von der Adobe Primetime-Authentifizierung bereitgestellt wird. Das Gerät sollte in der Lage sein, die eindeutige ID dauerhaft im lokalen Speicher zu speichern und die eindeutige ID als Geräte-ID anzugeben, wenn die Adobe Primetime-Authentifizierungs-APIs aufgerufen werden.
* Generieren digitaler Signaturen mit dem HMAC-SHA1-Algorithmus
* Festlegen beliebiger HTTP-Header
* RESTful-Webdienste nutzen
* XML- und JSON-Datenformate analysieren
* Traffic mithilfe von HTTPS senden
* Umgang mit HTTP-Fehlercodes
