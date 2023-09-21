---
description: Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 festlegen.
title: Schnelles Vorwärts- und Rückspulen implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# Schnelles Vorwärts- und Rückspulen implementieren {#implement-fast-forward-and-rewind}

Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 festlegen.

Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert festlegen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Wiedergabemodus, indem Sie die `rate` -Eigenschaft auf `MediaPlayer` auf einen zulässigen Wert.

   * Die `MediaPlayerItem` -Klasse definiert die zulässigen Wiedergaberaten.
   * TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.

     Wenn die Trickplay-Rate von 0 (Pause) oder 1 (normale Wiedergabe) in eine Rate geändert wird, die größer als 1 oder kleiner als -1 ist, werden alle Anzeigen auf der Timeline entfernt. Es gibt nur einen Zeitraum auf der gesamten Timeline, der eine Trickplay-Aktion erleichtert, damit der Inhalt schnell weitergeleitet und zurückgesetzt werden kann, ohne an einer Anzeigenposition anzuhalten. Diese Aktion wird durch eine Zeitleistensenkungsaktion auf TVSDK aktiviert, um alle aufgelösten adBreaks zu entfernen. Wenn die Trickplay-Wiedergabe bei 0 oder 1 fortgesetzt wird, werden die adBreaks zuerst durch die Aktion für Zeitleistenanhang wiederhergestellt.

     Beachten Sie die folgenden Informationen:

   * Wenn die Trickplay-Aktion den Inhalt zurückspulen soll, wird die Wiedergabe fortgesetzt, wenn die Rate auf 1 geändert wird.
   * Wenn die Trickplay-Aktion darin besteht, den Inhalt schnell weiterzuleiten, wird die zuletzt übersprungene adBreak an der Wiederaufnahmeposition wiedergegeben.

   In diesem Beispiel wird die interne Wiedergaberate des Players auf die angeforderte Rate gesetzt.

   ```
   private function onPlaybackRateChange(event:IndexChangeEvent):void { 
       var newRateIndex:int = event.newIndex; 
       var newRate:Number = _playbackRates[newRateIndex]; 
   
       _player.rate = newRate; 
   } 
   ```

1. Optional können Sie auf Ratenänderungs-Ereignisse warten, die Sie darüber informieren, wann Sie eine Ratenänderung angefordert haben und wann eine Ratenänderung tatsächlich stattfindet.

   TVSDK sendet die folgenden Ereignisse im Zusammenhang mit der Trick Play-Methode:

   * `mediacore.events.PlaybackRateEvent.RATE_SELECTED` wenn die `rate` ändert sich in einen anderen Wert.

   * `mediacore.events.PlaybackRateEvent.RATE_PLAYING` wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

   TVSDK sendet beide Ereignisse, wenn der Player aus dem Trick-Play-Modus in den normalen Wiedergabemodus zurückkehrt.

## API-Elemente für Ratenänderungen {#rate-change-api}

TVSDK enthält Methoden, Eigenschaften und Ereignisse zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit der schnellen Vorwärts- und Rückspaltung.

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `MediaPlayer.rate` Eigenschaft mit Setter- und Getter-Funktionen
* `MediaPlayer.localTime property` mit Getter-Funktion
* `mediacore.events.PlaybackRateEvent.RATE_SELECTED`
* `mediacore.events.PlaybackRateEvent.RATE_PLAYING`
* `MediaPlayerItem.IsTrickPlaySupported` Eigenschaft mit Getter-Funktion
* `AdBreakPlaybackEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.availablePlaybackRates` -Eigenschaft mit Getter-Funktion - gibt gültige Raten an.

| Kurswert | Auswirkung auf die Wiedergabe |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0  , 128.0 | Wechselt mit dem angegebenen Multiplikator schneller als normal in den Vorwärtsmodus (z. B. 4 ist viermal schneller als normal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0  , -128.0 | Wechselt in den Fast-Retail-Modus |
| 1.0 | Wechselt in den normalen Wiedergabemodus (Aufruf von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
| 0.0 | Pausen (aufrufen `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |

## Einschränkungen und Verhalten bei der Trickwiedergabe {#limitations-behavior-trick-play}

Hier finden Sie die Einschränkungen für den Trick Play-Modus:

* Die Master-Wiedergabeliste muss nur I-Frame-Segmente enthalten. Auf dem Bildschirm werden nur die Schlüsselrahmen der I-Frame-Spur angezeigt.
* Der Audio-Track und die Untertitel sind deaktiviert.
* Die Logik der adaptiven Bitrate (ABR) ist deaktiviert. TVSDK wählt eine Bitrate zwischen der niedrigsten bereitgestellten Rate und 800 Kbit/s aus und verwendet diese Rate während der gesamten Trick-Play-Sitzung.
* Wiedergabe und Pause sind aktiviert.
* Suche ist verboten. Um zu suchen, rufen Sie `pause` , um den Wiedergabemodus zu beenden, und rufen Sie dann `seek`.

* Sie können den Trick-Play-Modus in eine beliebige zulässige Wiedergabegeschwindigkeit (Wiedergabe oder Pause) beenden.
* Wenn Anzeigen in den Stream integriert werden:

   * Sie können nur während der Wiedergabe des Hauptinhalts zum Trick Play gehen. Ein Fehler wird ausgelöst, wenn Sie versuchen, während einer Werbeunterbrechung zu &quot;trick play&quot;zu wechseln.
   * Nach dem Starten des Trick Play-Modus werden die Werbeunterbrechungen ignoriert und es werden keine Anzeigenereignisse ausgelöst.
   * Die Zeitleiste, die TVSDK der Player-Anwendung zur Verfügung stellt, wird auch dann nicht geändert, wenn Werbeunterbrechungen übersprungen werden.
   * Die `MediaPlayer.currentTime` -Eigenschaft springt vorwärts (bei schneller Vorwärts) oder rückwärts (bei schneller Rückspaltung) mit der Dauer der übersprungenen Werbeunterbrechung. Durch dieses Sprungverhalten für die aktuelle Zeit kann die Stream-Dauer während der Trick Play-Zeit unverändert bleiben. Ihre Player-Anwendung kann `localTime` -Eigenschaft, um die Zeit zu verfolgen, die nur relativ zum Hauptinhalt ist. Für die Werte, die beim Überspringen einer Anzeige für die lokale Zeit zurückgegeben werden, werden keine Zeitpunkte ausgeführt.

   * Die `AdBreakPlaybackEvent.AD_BREAK_SKIPPED` -Ereignis unmittelbar bevor eine Werbeunterbrechung übersprungen wird. Ihr Player kann dieses Ereignis verwenden, um benutzerdefinierte Logik im Zusammenhang mit den übersprungenen Werbeunterbrechungen zu implementieren.
   * Beim Beenden der Suche wird dieselbe Richtlinie für die Anzeigenwiedergabe aufgerufen wie beim Beenden der Suche.

     Wie bei der Suche hängt das Verhalten daher davon ab, ob sich die Wiedergaberichtlinie Ihrer Anwendung von der standardmäßigen unterscheidet. Die Standardeinstellung ist, dass die letzte übersprungene Werbeunterbrechung an dem Punkt wiedergegeben wird, an dem Sie aus der Trickwiedergabe herausgekommen sind.
