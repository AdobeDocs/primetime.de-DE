---
description: Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.
seo-description: Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.
seo-title: Schnelles Vorwärts- und Zurückspulen implementieren
title: Schnelles Vorwärts- und Zurückspulen implementieren
uuid: bd190534-c871-4673-b79d-1413277f480f
translation-type: tm+mt
source-git-commit: 5a786d8001326f874a51d65b8e8badca44f46e96
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Schnelles Vorwärts- und Zurückspulen {#implement-fast-forward-and-rewind} implementieren

Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.

Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert einstellen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Wiedergabemodus, indem Sie die `rate`-Eigenschaft für `MediaPlayer` auf einen zulässigen Wert setzen.

   * Die `MediaPlayerItem`-Klasse definiert die zulässigen Wiedergaberaten.
   * TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.

      Wenn die Trickplay-Rate von 0 (Pause) oder 1 (normale Wiedergabe) in eine Rate geändert wird, die größer als 1 oder kleiner als -1 ist, werden alle Anzeigen in der Zeitleiste entfernt. Es gibt nur einen Punkt auf der gesamten Zeitschiene, der eine Trickplay-Aktion ermöglicht, damit der Inhalt schnell weitergeleitet und zurückgegeben werden kann, ohne an einer beliebigen Anzeigenposition anzuhalten. Diese Aktion wird durch eine Zeitschienen-Abtrennungsaktion auf TVSDK aktiviert, um alle aufgelösten adBreaks zu entfernen. Wenn das Trickplay bei 0 oder 1 fortgesetzt wird, werden die AdBreaks zuerst durch die Zeitschienenanlagenaktion wiederhergestellt.

      Beachten Sie die folgenden Informationen:

   * Wenn die Trickplay-Aktion den Inhalt zurückspulen soll, wird die Wiedergabe fortgesetzt, wenn die Rate auf 1 geändert wird.
   * Wenn bei der Trickplay-Aktion der Inhalt schnell weitergeleitet werden soll, wird das zuletzt übersprungene adBreak an der Wiederaufnahmeposition abgespielt.

   In diesem Beispiel wird die interne Wiedergaberate des Players auf die angeforderte Rate eingestellt.

   ```
   private function onPlaybackRateChange(event:IndexChangeEvent):void { 
       var newRateIndex:int = event.newIndex; 
       var newRate:Number = _playbackRates[newRateIndex]; 
   
       _player.rate = newRate; 
   } 
   ```

1. Sie können optional auf Ratenänderungen-Ereignis hören, die Sie darüber informieren, wann Sie eine Ratenänderung angefordert haben und wann tatsächlich eine Ratenänderung eintritt.

   TVSDK sendet die folgenden Ereignisse im Zusammenhang mit der Trickwiedergabe:

   * `mediacore.events.PlaybackRateEvent.RATE_SELECTED` wenn sich der  `rate` Wert in einen anderen Wert ändert.

   * `mediacore.events.PlaybackRateEvent.RATE_PLAYING` wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

   TVSDK löst beide Ereignis aus, wenn der Player vom Trick-Play-Modus zum normalen Wiedergabemodus zurückkehrt.

## API-Elemente für Ratenänderungen {#rate-change-api}

TVSDK umfasst Methoden, Eigenschaften und Ereignis zur Bestimmung gültiger Raten, aktueller Raten, zur Unterstützung von Trick Play und andere Funktionen im Zusammenhang mit dem schnellen Vor- und Zurückspulen.

Verwenden Sie die folgenden API-Elemente, um die Abspielraten zu ändern:

* `MediaPlayer.rate` Eigenschaft mit Setter- und Getter-Funktionen
* `MediaPlayer.localTime property` with getter function
* `mediacore.events.PlaybackRateEvent.RATE_SELECTED`
* `mediacore.events.PlaybackRateEvent.RATE_PLAYING`
* `MediaPlayerItem.IsTrickPlaySupported` Eigenschaft mit getter-Funktion
* `AdBreakPlaybackEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.availablePlaybackRates` -Eigenschaft mit Getter-Funktion - gibt gültige Raten an.

| Ratenwert | Auswirkungen auf die Wiedergabe |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Wechselt in den Vorwärtsmodus mit dem angegebenen Multiplikator schneller als normal (z. B. 4 ist viermal schneller als normal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0, -128.0 | Wechselt in den Modus &quot;Fast-Retwind&quot; |
| 1,0 | Wechselt in den normalen Wiedergabemodus (das Aufrufen von `play` entspricht dem Festlegen der rate-Eigenschaft auf 1,0) |
| 0,0 | Pausen (Aufrufen von `pause` entspricht dem Festlegen der rate-Eigenschaft auf 0,0) |

## Einschränkungen und Verhalten bei Trick Play {#limitations-behavior-trick-play}

Im Folgenden finden Sie die Einschränkungen für den Trick Play-Modus:

* Die Übergeordnet-Wiedergabeliste muss nur I-Frame-Segmente enthalten. Auf dem Bildschirm werden nur die Schlüsselbilder aus der I-Frame-Spur angezeigt.
* Die Audiospur und die Untertitel sind deaktiviert.
* Die Logik der adaptiven Bitrate (ABR) ist deaktiviert. TVSDK wählt eine Bitrate zwischen der niedrigsten bereitgestellten Rate und 800 Kbit/s aus und verwendet diese Rate während der gesamten Trick-Play-Sitzung.
* Wiedergabe und Pause sind aktiviert.
* Suche ist verboten. Um zu suchen, rufen Sie `pause` auf, um den Trick Play-Modus zu beenden, und rufen Sie dann `seek` auf.

* Sie können den Trick-Play-Modus in eine beliebige zulässige Wiedergabegeschwindigkeit (Wiedergabe oder Pause) beenden.
* Wenn Anzeigen in den Stream eingebunden werden:

   * Sie können nur zum Trick play gehen, während Sie den Hauptinhalt wiedergeben. Wenn Sie versuchen, während einer Werbeunterbrechung zu &quot;trick play&quot;zu wechseln, wird ein Fehler ausgelöst.
   * Nach dem Starten des Trick Play-Modus werden Werbeunterbrechungen ignoriert und es werden keine Ereignis ausgelöst.
   * Die Zeitleiste, die TVSDK der Player-Anwendung zur Verfügung stellt, wird auch dann nicht geändert, wenn Werbeunterbrechungen übersprungen werden.
   * Die `MediaPlayer.currentTime`-Eigenschaft springt mit der Dauer der übersprungenen Werbeunterbrechung vorwärts (bei schneller Vorwärtsbewegung) oder rückwärts (bei schnellem Zurückspulen). Durch dieses Sprungverhalten für die aktuelle Zeit bleibt die Stream-Dauer während der Trick-Wiedergabe unverändert. Ihre Player-Anwendung kann die `localTime`-Eigenschaft verwenden, um die Zeit relativ zum Hauptinhalt zu verfolgen. Für die Werte, die für die lokale Zeit zurückgegeben werden, wenn eine Anzeige übersprungen wird, werden keine Zeitsprünge ausgeführt.

   * Das `AdBreakPlaybackEvent.AD_BREAK_SKIPPED`-Ereignis wird unmittelbar vor dem Überspringen einer Werbeunterbrechung ausgelöst. Ihr Player kann dieses Ereignis verwenden, um benutzerdefinierte Logik in Bezug auf die übersprungenen Werbeunterbrechungen zu implementieren.
   * Beim Beenden der Trick-Wiedergabe werden dieselben Regeln für die Anzeigenwiedergabe aufgerufen wie beim Beenden der Suche.

      Wie bei der Suche hängt das Verhalten daher davon ab, ob sich die Wiedergaberichtlinie Ihrer Anwendung von der Standardrichtlinie unterscheidet. Die Standardeinstellung ist, dass die letzte übersprungene Werbeunterbrechung an dem Punkt wiedergegeben wird, an dem Sie die Trick-Wiedergabe beendet haben.