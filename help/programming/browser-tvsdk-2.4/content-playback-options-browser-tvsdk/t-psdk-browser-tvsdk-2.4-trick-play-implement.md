---
description: Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.
title: Schnelles Vorwärts- und Zurückspulen implementieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# Schnelles Vorwärts- und Zurückspulen{#implement-fast-forward-and-rewind} implementieren

Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.

>[!IMPORTANT]
>
>* Der Trick Play-Modus wird nur für MPEG Dash- und HLS VOD-Inhalte unterstützt.
>* Der Trick Play-Modus wird für Live-Streams oder Anzeigen nicht unterstützt.
>* Beim Wechsel vom Hauptinhalt zu einer Anzeige bleibt bei Browser TVSDK der Trick Play-Modus.

>



Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert einstellen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Trick-play-Modus, indem Sie die Rate für das `MediaPlayer` auf einen erlaubten Wert einstellen.

   * Die `MediaPlayerItem`-Klasse definiert die zulässigen Wiedergaberaten.
   * Browser TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.

      Die folgende Beispielfunktion legt die Rate fest:

      ```js
      setTrickPlayRate = function (player, trickPlayRate) { 
                    player.rate = trickPlayRate; 
      }
      ```

      Die folgende Beispielfunktion kann zur Abfrage der verfügbaren Wiedergaberaten verwendet werden:

      ```js
      getAvailableTrickPlayRates = function (player) { 
               var item = player.currentItem; 
               var availableRates = item. availablePlaybackRates; 
               return availableRates; 
      } 
      ```

1. Sie können optional auf Ratenänderungen-Ereignis hören, die Sie darüber informieren, wann Sie eine Ratenänderung angefordert haben und wann eine Ratenänderung tatsächlich stattfindet.

       Browser TVSDK sendet die folgenden Ereignisse im Zusammenhang mit der Trickwiedergabe:
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` wenn sich der  `rate` Wert in einen anderen Wert ändert.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

      Browser TVSDK löst beide Ereignis aus, wenn der Player vom Trick-Play-Modus zum normalen Play-Modus zurückkehrt.

## API-Elemente für Ratenänderungen {#rate-change-API-elements}

Browser TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit schnellen Vor- und Zurückspulen.

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates` - gibt gültige Raten an.

   | Ratenwert | Auswirkungen auf die Wiedergabe |
   |---|---|
   | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | Wechselt in den Vorwärtsmodus mit dem angegebenen Multiplikator schneller als normal (z. B. 4 ist viermal schneller als normal) |
   | -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 | Wechselt in den Modus &quot;Fast-Retwind&quot; |
   | 1,0 | Wechselt in den normalen Wiedergabemodus (das Aufrufen von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
   | 0,0 | Pausen (Aufrufen von `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |

## Einschränkungen und Verhalten bei Trick-play {#limitations-and-behavior-trick-play}

Es gibt einige Einschränkungen und einige Probleme in der Art und Weise, wie sich der Trick Play-Modus verhält.

Im Folgenden finden Sie eine Liste der Einschränkungen des Trick-Play-Modus:

* Wenn der Stream keine Anpassung der Trick-Wiedergabe enthält, wird die schnelle Rückspur deaktiviert und die maximale Wiedergabegeschwindigkeit für schnelle Vorspulen ist auf 8 begrenzt.
* Wenn Anpassungen der Trick-Wiedergabe verwendet werden, um den Trickmodus bereitzustellen, ist die Audiospur deaktiviert.
* Im Trick Play-Modus ist das Umschalten von Audio- und Untertitelspuren deaktiviert.
* Wiedergabe und Pause sind aktiviert.
* Wenn sich die Wiedergabe bei der Suche im Trick Play-Modus befindet, wird die Wiedergabegeschwindigkeit auf 1 eingestellt und die normale Wiedergabe wird fortgesetzt.
* Die Logik der adaptiven Bitrate (ABR) ist aktiviert.

   Bei normalen Anpassungen sind die Profil zwischen `ABRControlParameters.minBitRate` und `ABRControlParameters.maxBitRate` eingeschränkt. Bei der Verwendung von &quot;Trick Play&quot;-Anpassungen sind die Profil zwischen `ABRControlParameters.minTrickPlayBitRate` und `ABRControlParameters.maxTrickPlayBitRate` eingeschränkt.