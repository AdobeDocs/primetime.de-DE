---
title: CDN integrieren
description: CDN integrieren
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# CDN {#integrating-cdn} integrieren

Primetime Ad Insertion dient als Proxy zwischen Ihrer Client-Anwendung und Ihren Manifesten, nicht als Videoteil selbst. Stellen Sie Ihre Inhalte für das gewünschte CDN bereit und übergeben Sie die URL mithilfe der Bootstrap-API an Primetime Ad Insertion. Weitere Informationen zur Integration finden Sie unter [Unterstützte CDNs](/help/primetime-ad-insertion/technical-reference/supported-cdns.md).

## Unterstützte CDN-Tokenisierungssysteme {#cdn-tokenization-schemes}

CDNs verfügen oft über unterschiedliche Tokenisierungssysteme für die Fragmentautorisierung. Primetime-Ad Insertion unterstützt nativ wichtige CDN-Netze, darunter:

* Akamai
* Limelight
* Centurylink / Level3
* Wenden Sie sich an Ihren Primetime-Supportmitarbeiter, um eine vollständige Liste der unterstützten CDNs zu erhalten.

Weitere Informationen zum Parameter `pttoken` finden Sie unter [Bootstrap-API-Parameterbeschreibung](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md#parameter-description).

## Konfigurieren Sie Anzeigen, die aus dem Content CDN {#configure-ad-deliver-from-cdn} bereitgestellt werden sollen.

Möglicherweise möchten Sie Anzeigen und Inhalte desselben CDN bereitstellen, um die Affinität von Inhalten zu erhalten, Anzeigenblocker zu umgehen und/oder die Anzahl der erforderlichen Verbindungen aus der Clientanwendung zu optimieren. Primetime Ad Insertion unterstützt Fragment-Neuschreibungsregeln, um Fragmente Ihrem Content-CDN zuzuordnen. Weitere Informationen finden Sie unter [Manifestes Umschreiben](/help/primetime-ad-insertion/technical-reference/manifest-rewriting.md).

## Verbessern Sie die Beginn-up-Leistung mit Ihrem CDN {#increase-startup-performance}

Weitere Informationen finden Sie unter [Optimieren des Beginns](/help/primetime-ad-insertion/best-practices/optimize-video-startup-time.md).

## Multi-CDN-Funktionen {#enable-multi-cdn-fetures}

Wenden Sie sich an Ihren Primetime-Support-Mitarbeiter, um Multi-CDN-Funktionen zu aktivieren.
