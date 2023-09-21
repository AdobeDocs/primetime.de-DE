---
title: Überwachen der Adobe Primetime-Authentifizierung
description: Überwachen der Adobe Primetime-Authentifizierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Überwachen der Adobe Primetime-Authentifizierung {#monitoring-adobe-primetime-authentication}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Einführung {#intro}

Kunden können [Nagios](http://www.nagios.org) oder anderen Tools, um zu überprüfen, ob die Adobe Primetime-Authentifizierung aktiviert oder deaktiviert ist.

## Überwachen von Endpunkten {#monitoring-endpoints}

### Zu überwachende Endpunkte {#endpoints-to-monitor}

* Der Konfigurationsendpunkt für alle Plattformen: `https://sp.auth.adobe.com/adobe-services/config/[your-config-ID]`- Es ist entweder über HTTP oder HTTPS verfügbar (je nach Auswahl durch den Entwickler des Inhaltsanbieters). Wenn dieser Endpunkt fehlt, bedeutet das, dass Ihr Inhalt nicht auf allen Plattformen und MVPDs verfügbar ist. Für die clientlose REST-API haben wir auch den folgenden Endpunkt:  `https://api.auth.adobe.com/adobe-services/config your-config-ID]`.

* Die folgenden Endpunkte sind Teil des Adobe Primetime Authentication Web SDK.  Wenn es fehlt, bedeutet dies, dass Pay-TVpass für alle Programmierer und alle Webeigenschaften deaktiviert ist:

   * `https://entitlement.auth.adobe.com/entitlement/v4/AccessEnabler.js`
   * `https://entitlement.auth.adobe.com/entitlement/js/AccessEnabler.js`


### Endpunkte, die Sie nicht überwachen sollten {#endpoints-not-monitor}

* `https://sp.auth.adobe.com/sp/saml/SAMLAssertionConsumer`

  Sie erhalten immer einen 503-Fehler, da dieser Endpunkt eine MVPD SAML-Antwort darauf benötigt.

* Andere Entitäts-Endpunkte - `adobe-services/1.0/authenticate/`, `adobe-services/1.0/deviceShortAuthorize`, `adobe-services/1.0/authorize`

Sie können diese Endpunkte nicht überwachen, da sie eine Payload für eine relevante Antwort benötigen.
