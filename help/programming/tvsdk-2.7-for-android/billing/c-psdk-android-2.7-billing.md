---
description: Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.
seo-description: Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.
seo-title: Rechnungsmetriken
title: Rechnungsmetriken
uuid: 4a03995a-60f6-440e-9cdf-9c0b9c5f1d90
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Übersicht {#billing-metrics-overview}

Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.

Jedes Mal, wenn der Player ein Stream-Beginn-Ereignis generiert, senden TVSDK-Beginn HTTP-Nachrichten regelmäßig an das Rechnungssystem der Adobe. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann für standardmäßige VOD-, Pro-VOD- (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterschiedlich sein. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, Ihr Vertrag mit der Adobe legt die tatsächlichen Werte fest.

Die Meldungen enthalten die folgenden Informationen:

* Inhaltstyp (live, linear oder VOD)
* Inhalts-URL
* Ob Anzeigen aktiviert sind
* Ob Mid-Roll-Anzeigen aktiviert sind (nur VOD)
* Ob der Stream durch DRM geschützt ist
* TVSDK-Version und -Plattform

Adobe konfiguriert diese Anordnung im Voraus, Sie können jedoch mit Ihrem Adobe Enablement-Kundenbetreuer zusammenarbeiten, um die Anordnung zu ändern, und mit Ihrem Kundenbetreuer für die Adobe-Aktivierung zusammenarbeiten.

Um die Statistiken zu überwachen, die TVSDK an die Adobe sendet, rufen Sie die URL von Ihrem Kundenbetreuer für Adobe-Aktivierung ab und verwenden Sie ein Netzwerk-Erfassungswerkzeug wie Charles, um die Daten anzuzeigen.
