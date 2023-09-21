---
title: Zwischenspeicherung
description: Zwischenspeicherung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# HTTP-Zwischenspeicherung {#caching}

Beim Primetime-Ad Insertion werden beim Abrufen von Anzeigenkreativen und Inhalten standardmäßig HTTP-Cache-Steuerelement-Header berücksichtigt.  Dies kann die Anzahl der Netzwerkanforderungen drastisch reduzieren, die Primetime Ad Insertion zum CDN für alle Clients benötigt.  Für die Zwischenspeicherung empfiehlt Adobe die folgenden Einstellungen und das Senden des HTTP-Headers `max-age` von Ihrem CDN aus.  Wenden Sie sich an Ihren CDN-Support-Mitarbeiter, um diese Header in Ihren Video-Streams und Anzeigen-Streams zu aktivieren.

## Für Live-/Linear-Inhalte {#caching-live-linear-content}

* Master-Manifest: 24 Stunden oder Cache-Control: max-age=86400
* Medienmanifest: 1 Sekunde oder Cache-Control: max-age=1

## Für VOD-Inhalt {#caching-vod-content}

* Master-Manifest: 24 Stunden oder Cache-Control: max-age=86400
* Medienmanifest: 24 Stunden oder Cache-Control: max-age=86400
