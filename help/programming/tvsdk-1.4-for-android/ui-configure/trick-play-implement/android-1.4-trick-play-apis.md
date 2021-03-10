---
description: TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit dem schnellen Vor- und Zurückspulen.
title: API-Elemente für Ratenänderungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%

---


# API-Elemente für Ratenänderungen{#rate-change-api-elements}

TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit dem schnellen Vor- und Zurückspulen.

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates` - gibt gültige Raten an.

| Ratenwert | Auswirkungen auf die Wiedergabe |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Wechselt in den Vorwärtsmodus mit dem angegebenen Multiplikator schneller als normal (z. B. 4 ist viermal schneller als normal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0, -128.0 | Wechselt in den Modus &quot;Fast-Retwind&quot; |
| 1,0 | Wechselt in den normalen Wiedergabemodus (das Aufrufen von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
| 0,0 | Pausen (Aufrufen von `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |

