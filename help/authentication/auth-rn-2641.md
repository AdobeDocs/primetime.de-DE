---
title: Versionshinweise zur Adobe Primetime-Authentifizierung 2.6.4.1
description: Versionshinweise zur Adobe Primetime-Authentifizierung 2.6.4.1
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Versionshinweise zur Adobe Primetime-Authentifizierung 2.6.4.1 {#authn-264-rn}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

Auf dieser Seite werden neue Funktionen, Änderungen und bekannte Probleme in dieser Version beschrieben:

## Server-seitige und Web-Clients {#server-side-web-clients-2641}

* [Build-Nummer](#build-number-2641)
* [Versionsübersicht](#release-overview-2641)

### Build-Nummer {#build-number-2641}

Adobe Primetime-Authentifizierung: adobe-pass-**2,64,1**
Releasedatum: **01/31/2023 - 02/02/2023**

### Versionsübersicht {#release-overview-2641}

Diese Version fügt Folgendes hinzu:

* Die Möglichkeit, nicht angeforderte Authentifizierungsantworten von MVPDs zu blockieren, bei denen der Parameter &quot;in_response_to&quot;in der SAML-Assertion fehlt.
* Eine verbesserte Validierung des Parameters redirect_url , um die Sicherheitsanforderungen zu erfüllen.
* Eine verbesserte Protokollierung der Geräteinformationen für Authentifizierungsanfragen für den zweiten Bildschirm mithilfe von Informationen, die vom ursprünglichen Gerät bereitgestellt werden.
