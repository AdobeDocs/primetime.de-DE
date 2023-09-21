---
title: Versionshinweise zur Adobe Primetime-Authentifizierung 2.64
description: Versionshinweise zur Adobe Primetime-Authentifizierung 2.64
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Versionshinweise zur Adobe Primetime-Authentifizierung 2.64 {#authn-264-rn}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

Auf dieser Seite werden neue Funktionen, Änderungen und bekannte Probleme in dieser Version beschrieben:

## Server-seitige und Web-Clients {#ss-web-clients}

* [Build-Nummer](#build-no-264)
* [Neue Funktionen](#new-featres-264)
* [Fehlerbehebungen](#bug-fixes-264)


### Build-Nummer {#build-no-264}

Adobe Primetime-Authentifizierung: adobe-pass-**2,64**

Releasedatum: **11/08/2022 - 11/10/2022**

### Neue Funktionen {#new-featres-264}

* Aktualisierungen der Infrastruktur, die darauf abzielen, die Reaktionszeiten der Server zu verkürzen und die Gesamtleistung des Systems zu verbessern.
* Verbesserungen des neuen Mechanismus zur Identifizierung der Plattform.
* Möglichkeit, nicht angeforderte Authentifizierungsantworten von MVPDs zu blockieren, bei denen der Parameter &quot;in_response_to&quot;in der SAML-Assertion fehlt.

### Fehlerbehebungen {#bug-fixes-264}

* Fehlerkorrektur - Die falsche Formatierung einiger veralteter TempPass-Token wurde korrigiert.
* Es wurden kleinere Probleme beim zweiten Bildschirm-Authentifizierungsfluss behoben.
