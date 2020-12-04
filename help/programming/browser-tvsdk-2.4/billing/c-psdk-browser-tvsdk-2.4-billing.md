---
description: Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.
seo-description: Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.
seo-title: Rechnungsmetriken
title: Rechnungsmetriken
uuid: e09b77b3-89d3-44d6-be4e-e1612fbf89fc
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Übersicht {#billing-metrics-overview}

Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.

Jedes Mal, wenn der Player ein Stream-Beginn-Ereignis generiert, Browser TVSDK-Beginn, um HTTP-Nachrichten regelmäßig an das Rechnungssystem der Adobe zu senden. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann für standardmäßige VOD-, Pro-VOD- (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterschiedlich sein. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, Ihr Vertrag mit der Adobe legt die tatsächlichen Werte fest.

Die Meldungen enthalten die folgenden Informationen:

* Inhaltstyp (live, linear oder VOD)
* Inhalts-URL
* Ob Anzeigen aktiviert sind
* Ob Mid-Roll-Anzeigen aktiviert sind (nur VOD)
* Ob der Stream durch DRM geschützt ist
* Browser TVSDK-Version und -Plattform

Adobe konfiguriert diese Anordnung vorab. Wenn Sie die Anordnung jedoch ändern möchten, wenden Sie sich an Ihren Kundenbetreuer für Adobe-Aktivierung.

Um die Statistiken zu überwachen, die Browser TVSDK an die Adobe sendet, rufen Sie die URL von Ihrem Kundenbetreuer ab und verwenden Sie ein Netzwerk-Erfassungswerkzeug, z. B. Charles, um die Daten anzuzeigen.
