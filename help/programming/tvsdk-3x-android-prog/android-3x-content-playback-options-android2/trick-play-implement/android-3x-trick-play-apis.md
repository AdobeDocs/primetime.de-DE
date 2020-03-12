---
description: TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen, die sich auf schnelle Vorwärts- und Rückspulen beziehen.
seo-description: TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen, die sich auf schnelle Vorwärts- und Rückspulen beziehen.
seo-title: API-Elemente für Ratenänderungen
title: API-Elemente für Ratenänderungen
uuid: c2bcd20c-0641-4d75-802c-08098786d572
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

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
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Wechselt in den Modus &quot;Fast-Retwind&quot; |
| 1.0 | Wechselt in den normalen Wiedergabemodus (Aufruf `play` entspricht dem Einstellen der rate-Eigenschaft auf 1,0) |
| 0.0 | Pausen (Aufruf `pause` entspricht dem Einstellen der rate-Eigenschaft auf 0,0) |