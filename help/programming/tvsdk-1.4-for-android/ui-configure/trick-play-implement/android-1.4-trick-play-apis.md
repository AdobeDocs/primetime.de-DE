---
description: TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit dem schnellen Vor- und Zurückspulen.
seo-description: TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit dem schnellen Vor- und Zurückspulen.
seo-title: API-Elemente für Ratenänderungen
title: API-Elemente für Ratenänderungen
uuid: 0040d35c-f9cb-4066-9bee-828ed5541194
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 2%

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

