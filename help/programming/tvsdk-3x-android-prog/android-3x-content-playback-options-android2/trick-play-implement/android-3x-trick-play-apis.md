---
description: TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen, die sich auf schnelle Vorwärts- und Rückspulen beziehen.
title: API-Elemente für Ratenänderungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%

---


# API-Elemente für Ratenänderungen {#rate-change-api-elements}

TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen, die sich auf schnelle Vorwärts- und Rückspulen beziehen.

<!--<a id="section_E5D37C71323947E2AED8B866D9835E31"></a>-->

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `PlaybackRateEvent.getRate`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.isTrickPlaySupported`
* `MediaPlayerItem.getAvailablePlaybackRates`, der gültige Raten angibt.

| **Ratenwert** | **Auswirkungen auf die Wiedergabe** |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Wechselt in den Vorwärtsmodus mit dem angegebenen Multiplikator schneller als normal (z. B. 4 ist viermal schneller als normal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0, -128.0 | Wechselt in den Modus &quot;Fast-Retwind&quot; |
| 1,0 | Wechselt in den normalen Wiedergabemodus (das Aufrufen von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
| 0,0 | Pausen (Aufrufen von `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |