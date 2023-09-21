---
title: CDN integrieren
description: Integrieren Ihres CDN
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# CDN integrieren {#integrating-cdn}

Primetime Ad Insertion dient als Proxy zwischen Ihrer Client-Anwendung und den Manifesten, nicht als Videoblock selbst. Stellen Sie Ihren Inhalt in das gewünschte CDN bereit und übergeben Sie die URL mithilfe der Bootstrap-API an Primetime Ad Insertion. Informationen zur Integration finden Sie unter [Unterstützte CDNs](/help/primetime-ad-insertion/technical-reference/supported-cdns.md).

## Unterstützte CDN-Tokenisierungssysteme {#cdn-tokenization-schemes}

CDNs verfügen oft über verschiedene Tokenisierungssysteme für die Fragmentautorisierung. Primetime Ad Insertion unterstützt nativ wichtige CDN-Netzwerke, darunter:

* Akamai
* Limelight
* Centurylink / Level3
* Wenden Sie sich an Ihren Primetime-Support-Mitarbeiter, um eine vollständige Liste der unterstützten CDNs zu erhalten.

Weitere Informationen zum `pttoken` Parameter, siehe [Bootstrap-API-Parameterbeschreibung](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md#parameter-description).

## Konfigurieren von Anzeigen zur Bereitstellung über das Content CDN {#configure-ad-deliver-from-cdn}

Möglicherweise möchten Sie Anzeigen und Inhalte aus demselben CDN bereitstellen, um die Content-Affinität zu wahren, die Umgehung von Anzeigenblockern und/oder die Optimierung der Anzahl der erforderlichen Verbindungen aus der Clientanwendung zu unterstützen. Primetime Ad Insertion unterstützt das Umschreiben von Fragmenten, um Fragmente Ihrem Inhalts-CDN zuzuordnen. Weitere Informationen finden Sie unter [Neuschreiben des Manifests](/help/primetime-ad-insertion/technical-reference/manifest-rewriting.md).

## Verbessern der Start-up-Leistung mit Ihrem CDN {#increase-startup-performance}

Weitere Informationen finden Sie unter [Optimieren des Start-ups](/help/primetime-ad-insertion/best-practices/optimize-video-startup-time.md).

## Multi-CDN-Funktionen {#enable-multi-cdn-fetures}

Wenden Sie sich an Ihren Primetime-Support-Mitarbeiter, um Multi-CDN-Funktionen zu aktivieren.
