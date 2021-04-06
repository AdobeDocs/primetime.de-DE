---
title: Zwischenspeicherung
description: Zwischenspeicherung
copied-description: true
exl-id: c12c2345-db55-468a-b4b5-5a9e1364a46d
translation-type: tm+mt
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# HTTP-Zwischenspeicherung {#caching}

Primetime-Ad Insertion berücksichtigt standardmäßig HTTP-Cache-Steuerungsheader beim Abrufen von Werbeinhaltern sowie von Inhalten.  Dadurch kann die Anzahl der Netzwerkanforderungen, die Primetime Ad Insertion für das CDN benötigt, drastisch reduziert werden.  Für die Zwischenspeicherung empfiehlt Adobe die folgenden Einstellungen und das Senden des HTTP-Headers `max-age` aus Ihrem CDN.  Wenden Sie sich an Ihren CDN-Kundenbetreuer, um diese Header in Ihren Video- und Anzeigenströmen zu aktivieren.

## Für Live-/Lineare Inhalte {#caching-live-linear-content}

* Übergeordnet-Manifest: 24 Stunden oder Cache-Steuerung: max-age=86400
* Medienmanifest: 1 Sekunde oder Cache-Steuerung: max-age=1

## Für VOD-Inhalt {#caching-vod-content}

* Übergeordnet-Manifest: 24 Stunden oder Cache-Steuerung: max-age=86400
* Medienmanifest: 24 Stunden oder Cache-Steuerung: max-age=86400
