---
description: TVSDK enthält Methoden, Eigenschaften und Ereignisse zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit der schnellen Vorwärts- und Rückspaltung.
title: API-Elemente für Ratenänderungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%

---

# API-Elemente für Ratenänderungen{#rate-change-api-elements}

TVSDK enthält Methoden, Eigenschaften und Ereignisse zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit der schnellen Vorwärts- und Rückspaltung.

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates` - gibt gültige Tarife an.

| Kurswert | Auswirkung auf die Wiedergabe |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Wechselt mit dem angegebenen Multiplikator schneller als normal in den Vorwärtsmodus (z. B. 4 ist viermal schneller als normal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Wechselt in den Fast-Retail-Modus |
| 1.0 | Wechselt in den normalen Wiedergabemodus (Aufruf von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
| 0.0 | Pausen (aufrufen `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |
