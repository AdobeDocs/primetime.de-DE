---
description: Um Kunden, die nur für die von ihnen verwendeten Artikel bezahlen möchten, anstatt für einen festen Preis unabhängig von der tatsächlichen Verwendung zu bezahlen, sammelt Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel die Kunden bezahlen müssen.
seo-description: Um Kunden, die nur für die von ihnen verwendeten Artikel bezahlen möchten, anstatt für einen festen Preis unabhängig von der tatsächlichen Verwendung zu bezahlen, sammelt Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel die Kunden bezahlen müssen.
seo-title: Rechnungsmetriken
title: Rechnungsmetriken
uuid: 6ae9eb1e-4b03-467f-b80a-96313bd01543
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Rechnungsmetriken {#billing-metrics}

Um Kunden, die nur für die von ihnen verwendeten Artikel bezahlen möchten, anstatt für einen festen Preis unabhängig von der tatsächlichen Verwendung zu bezahlen, sammelt Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel die Kunden bezahlen müssen.

Jedes Mal, wenn der Player ein Stream-Beginn-Ereignis generiert, senden TVSDK-Beginn HTTP-Nachrichten regelmäßig an das Rechnungssystem von Adobe. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann für standardmäßige VOD-, Pro-VOD- (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterschiedlich sein. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, aber Ihr Vertrag mit Adobe legt die tatsächlichen Werte fest.

Die Meldungen enthalten die folgenden Informationen:

* Inhaltstyp (live, linear oder VOD)
* Inhalts-URL
* Ob Anzeigen aktiviert sind
* Ob Mid-Roll-Anzeigen aktiviert sind (nur VOD)
* Ob der Stream durch DRM geschützt ist
* TVSDK-Version und -Plattform

Diese Vereinbarung wird von Adobe vorkonfiguriert. Sie können jedoch mit Ihrem Adobe-Kundenbetreuer zusammenarbeiten, um die Vereinbarung zu ändern, und mit Ihrem Adobe-Kundenbetreuer zusammenarbeiten.

Um die Statistiken zu überwachen, die TVSDK an Adobe sendet, rufen Sie die URL von Ihrem Adobe-Kundenbetreuer ab und verwenden Sie ein Netzwerk-Erfassungswerkzeug wie Charles, um die Daten anzuzeigen.