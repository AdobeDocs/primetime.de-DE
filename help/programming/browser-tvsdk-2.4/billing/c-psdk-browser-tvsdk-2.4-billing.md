---
description: Um Kunden, die nur für die von ihnen verwendeten Artikel bezahlen möchten, anstatt für einen festen Preis unabhängig von der tatsächlichen Verwendung zu bezahlen, sammelt Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel die Kunden bezahlen müssen.
seo-description: Um Kunden, die nur für die von ihnen verwendeten Artikel bezahlen möchten, anstatt für einen festen Preis unabhängig von der tatsächlichen Verwendung zu bezahlen, sammelt Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel die Kunden bezahlen müssen.
seo-title: Rechnungsmetriken
title: Rechnungsmetriken
uuid: e09b77b3-89d3-44d6-be4e-e1612fbf89fc
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Übersicht {#billing-metrics-overview}

Um Kunden, die nur für die von ihnen verwendeten Artikel bezahlen möchten, anstatt für einen festen Preis unabhängig von der tatsächlichen Verwendung zu bezahlen, sammelt Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel die Kunden bezahlen müssen.

Jedes Mal, wenn der Player ein Stream-Beginn-Ereignis generiert, senden Browser TVSDK-Beginn HTTP-Nachrichten regelmäßig an das Rechnungssystem von Adobe. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann für standardmäßige VOD-, Pro-VOD- (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterschiedlich sein. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, aber Ihr Vertrag mit Adobe legt die tatsächlichen Werte fest.

Die Meldungen enthalten die folgenden Informationen:

* Inhaltstyp (live, linear oder VOD)
* Inhalts-URL
* Ob Anzeigen aktiviert sind
* Ob Mid-Roll-Anzeigen aktiviert sind (nur VOD)
* Ob der Stream durch DRM geschützt ist
* Browser TVSDK-Version und -Plattform

Adobe konfiguriert diese Vereinbarung zwar vorab, sollte Sie sich jedoch an Ihren Adobe-Kundenbetreuer wenden, um die Vereinbarung zu ändern.

Um die Statistiken zu überwachen, die Browser TVSDK an Adobe sendet, rufen Sie die URL von Ihrem Adobe-Kundenbetreuer ab und verwenden Sie ein Netzwerk-Erfassungswerkzeug, z. B. Charles, um die Daten anzuzeigen.
