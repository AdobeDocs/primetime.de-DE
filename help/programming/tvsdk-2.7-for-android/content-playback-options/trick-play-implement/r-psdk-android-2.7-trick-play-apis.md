---
description: TVSDK enthält Methoden, Eigenschaften und Ereignisse zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen, die sich auf schnelle Vorwärts- und Rückspaltung beziehen.
title: API-Elemente für Ratenänderungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%

---

# API-Elemente für Ratenänderungen {#rate-change-api-elements}

TVSDK enthält Methoden, Eigenschaften und Ereignisse zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen, die sich auf schnelle Vorwärts- und Rückspaltung beziehen.

<!--<a id="section_E5D37C71323947E2AED8B866D9835E31"></a>-->

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `PlaybackRateEvent.getRate`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.isTrickPlaySupported`
* `MediaPlayerItem.getAvailablePlaybackRates`, der gültige Raten angibt.

| Kurswert | Auswirkung auf die Wiedergabe |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Wechselt mit dem angegebenen Multiplikator schneller als normal in den Vorwärtsmodus (z. B. 4 ist viermal schneller als normal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Wechselt in den Fast-Retail-Modus |
| 1.0 | Wechselt in den normalen Wiedergabemodus (Aufruf von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
| 0.0 | Pausen (aufrufen `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |
