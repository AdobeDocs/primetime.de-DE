---
description: Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 festlegen.
title: Schnelles Vorwärts- und Rückspulen implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Schnelles Vorwärts- und Rückspulen implementieren{#implement-fast-forward-and-rewind}

Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 festlegen.

>[!IMPORTANT]
>
>* Der Trick Play-Modus wird nur für MPEG Dash- und HLS VOD-Inhalte unterstützt.
>* Der Trick Play-Modus wird für Live-Streams oder Anzeigen nicht unterstützt.
>* Beim Wechsel vom Hauptinhalt zu einer Anzeige verlässt Browser TVSDK den Modus &quot;Trick Play&quot;.
>

Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert festlegen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Wiedergabemodus, indem Sie die Rate auf der `MediaPlayer` auf einen zulässigen Wert.

   * Die `MediaPlayerItem` -Klasse definiert die zulässigen Wiedergaberaten.
   * Browser TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.

     Die folgende Beispielfunktion legt die Rate fest:

     ```js
     setTrickPlayRate = function (player, trickPlayRate) { 
                   player.rate = trickPlayRate; 
     }
     ```

     Mit der folgenden Beispielfunktion können Sie die verfügbaren Wiedergabequoten abfragen:

     ```js
     getAvailableTrickPlayRates = function (player) { 
              var item = player.currentItem; 
              var availableRates = item. availablePlaybackRates; 
              return availableRates; 
     } 
     ```

1. Optional können Sie auf Ratenänderungs-Ereignisse warten, die Sie darüber informieren, wann Sie eine Ratenänderung angefordert haben und wann eine Ratenänderung tatsächlich stattfindet.

       Browser TVSDK sendet die folgenden Ereignisse im Zusammenhang mit der Trickwiedergabe:
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` wenn die `rate` ändert sich in einen anderen Wert.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

     Browser TVSDK sendet beide Ereignisse, wenn der Player aus dem Trick-Play-Modus in den normalen Wiedergabemodus zurückkehrt.

## API-Elemente für Ratenänderungen {#rate-change-API-elements}

Browser TVSDK enthält Methoden, Eigenschaften und Ereignisse, um gültige Raten, aktuelle Raten, die Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit der schnellen Vorwärts- und Rückspaltung zu ermitteln.

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates` - gibt gültige Tarife an.

  | Kurswert | Auswirkung auf die Wiedergabe |
  |---|---|
  | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | Wechselt mit dem angegebenen Multiplikator schneller als normal in den Vorwärtsmodus (z. B. 4 ist viermal schneller als normal) |
  | -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 | Wechselt in den Fast-Retail-Modus |
  | 1.0 | Wechselt in den normalen Wiedergabemodus (Aufruf von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
  | 0.0 | Pausen (aufrufen `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |

## Einschränkungen und Verhalten bei Trick-play {#limitations-and-behavior-trick-play}

Es gibt einige Einschränkungen und einige Probleme in der Art, wie sich der Trick Play-Modus verhält.

Im Folgenden finden Sie eine Liste der Einschränkungen für den Trick-Play-Modus:

* Wenn der Stream keine Anpassung der Trickwiedergabe enthält, wird die schnelle Rückspaltung deaktiviert und die maximale Wiedergabedatei für schnelle Vorwärts ist auf 8 beschränkt.
* Wenn Anpassungen der Trickwiedergabe verwendet werden, um den Trickmodus bereitzustellen, ist der Audio-Track deaktiviert.
* Im Trick Play-Modus ist das Wechseln von Audio- und Untertitelspuren deaktiviert.
* Wiedergabe und Pause sind aktiviert.
* Wenn sich die Wiedergabe bei der Suche im Modus &quot;Trick Play&quot;befindet, wird die Wiedergaberate auf 1 gesetzt und die normale Wiedergabe wird fortgesetzt.
* Die Logik der adaptiven Bitrate (ABR) ist aktiviert.

  Bei normalen Anpassungen sind die Profile zwischen `ABRControlParameters.minBitRate` und `ABRControlParameters.maxBitRate`. Bei der Verwendung von Anpassungen der Trickwiedergabe sind die Profile zwischen `ABRControlParameters.minTrickPlayBitRate` und `ABRControlParameters.maxTrickPlayBitRate`.
