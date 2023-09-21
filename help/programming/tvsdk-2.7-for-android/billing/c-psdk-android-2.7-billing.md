---
description: Um Kunden aufzunehmen, die nur für das bezahlen möchten, was sie verwenden, anstatt für einen festen Satz, unabhängig von der tatsächlichen Verwendung, erfasst Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel Kunden abrechnen müssen.
title: Abrechnungsmetriken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Übersicht {#billing-metrics-overview}

Um Kunden aufzunehmen, die nur für das bezahlen möchten, was sie verwenden, anstatt für einen festen Satz, unabhängig von der tatsächlichen Verwendung, erfasst Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel Kunden abrechnen müssen.

Jedes Mal, wenn der Player ein Stream-Startereignis generiert, beginnt TVSDK mit dem regelmäßigen Versand von HTTP-Nachrichten an das Adobe-Abrechnungssystem. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann sich für standardmäßige VOD, Pro VOD (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterscheiden. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, Ihr Vertrag mit Adobe bestimmt jedoch die tatsächlichen Werte.

Die Nachrichten enthalten die folgenden Informationen:

* Inhaltstyp (live, linear oder VOD)
* Inhalts-URL
* Ob Anzeigen aktiviert sind
* Ob Mid-Roll-Anzeigen aktiviert sind (nur VOD)
* Ob der Stream durch DRM geschützt wird
* TVSDK-Version und -Plattform

Adobe konfiguriert diese Anordnung vorab. Sie können jedoch mit Ihrem Adobe-Aktivierungsbeauftragten zusammenarbeiten, um die Anordnung zu ändern, und mit Ihrem Adobe-Aktivierungsbeauftragten zusammenarbeiten.

Um die Statistiken zu überwachen, die TVSDK an Adobe sendet, rufen Sie die URL von Ihrem Adobe-Aktivierungsbeauftragten ab und verwenden Sie ein Netzwerk-Erfassungswerkzeug wie Charles, um die Daten anzuzeigen.
