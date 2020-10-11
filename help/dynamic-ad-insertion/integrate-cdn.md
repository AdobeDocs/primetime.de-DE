---
title: CDN integrieren
description: CDN integrieren
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# CDN integrieren {#integrating-cdn}

Primetime Ad Insertion dient als Proxy zwischen Ihrer Client-Anwendung und Ihren Manifesten, nicht als Videoteil selbst. Stellen Sie Ihre Inhalte für das gewünschte CDN bereit und übergeben Sie die URL mithilfe der Bootstrap-API an Primetime Ad Insertion.<!-- For integration details, see [Supported CDNs](supported-cdns.md).-->

## Unterstützte CDN-Tokenisierungsprogramme {#cdn-tokenization-schemes}

CDNs verfügen oft über unterschiedliche Tokenisierungssysteme für die Fragmentautorisierung. Primetime-Ad Insertion unterstützt nativ wichtige CDN-Netze, darunter:

* Akamai
* Limelight
* Centurylink / Level3
* Wenden Sie sich an Ihren Primetime-Supportmitarbeiter, um eine vollständige Liste der unterstützten CDNs zu erhalten.

Weitere Informationen zum `pttoken` Parameter finden Sie unter Parameterbeschreibung für die [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md).

## Konfigurieren von Anzeigen, die vom Content CDN bereitgestellt werden {#configure-ad-deliver-from-cdn}

Möglicherweise möchten Sie Anzeigen und Inhalte desselben CDN bereitstellen, um die Affinität von Inhalten zu erhalten, Anzeigenblocker zu umgehen und/oder die Anzahl der erforderlichen Verbindungen aus der Clientanwendung zu optimieren. Primetime Ad Insertion unterstützt Fragment-Neuschreibungsregeln, um Fragmente Ihrem Content-CDN zuzuordnen.

<!--## Increase start-up performance with your CDN {#increase-startup-performance}

For more information, see [Optimizing start-up](optimize-video-startup-time.md).-->

## Multi-CDN-Funktionen {#enable-multi-cdn-fetures}

Wenden Sie sich an Ihren Primetime-Support-Mitarbeiter, um Multi-CDN-Funktionen zu aktivieren.
