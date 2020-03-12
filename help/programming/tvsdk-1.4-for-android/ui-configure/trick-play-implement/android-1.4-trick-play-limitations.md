---
description: Es gibt einige Einschränkungen und einige Probleme in der Art und Weise, wie sich der Trick Play-Modus verhält.
seo-description: Es gibt einige Einschränkungen und einige Probleme in der Art und Weise, wie sich der Trick Play-Modus verhält.
seo-title: Einschränkungen und Verhalten bei der Trick-Wiedergabe
title: Einschränkungen und Verhalten bei der Trick-Wiedergabe
uuid: 0e84c9ef-fc18-4667-ad17-7f4777b552ba
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Einschränkungen und Verhalten bei der Trick-Wiedergabe{#limitations-and-behavior-for-trick-play}

Es gibt einige Einschränkungen und einige Probleme in der Art und Weise, wie sich der Trick Play-Modus verhält.

<!--<a id="section_8B88E281A0FA4661B4C2C70A0ABED57C"></a>-->

Im Folgenden finden Sie die Einschränkungen für den Trick Play-Modus:

* Die Master-Playlist muss nur I-Frame-Segmente enthalten. Auf dem Bildschirm werden nur die Schlüsselbilder aus der I-Frame-Spur angezeigt.
* Die Audiospur und die Untertitel sind deaktiviert.
* Die Logik der adaptiven Bitrate (ABR) ist deaktiviert. TVSDK wählt eine Bitrate zwischen der niedrigsten bereitgestellten Rate und 800 Kbit/s aus und verwendet diese Rate während der gesamten Trick-Play-Sitzung.
* Wiedergabe und Pause sind aktiviert.
* Suche ist verboten. Um zu suchen, rufen Sie `pause` zum Beenden des Trick Play-Modus auf und rufen Sie dann `seek`.

* Sie können vom Trick Play-Modus zu einer beliebigen zulässigen Wiedergabegeschwindigkeit (Wiedergabe oder Pause) wechseln.
* Wenn Anzeigen in den Stream eingebunden werden:

   * Sie können nur zum Trick play gehen, während Sie den Hauptinhalt wiedergeben. Wenn Sie versuchen, während einer Werbeunterbrechung zu &quot;trick play&quot;zu wechseln, wird ein Fehler ausgelöst.
   * Nach dem Starten des Trick Play-Modus werden Werbeunterbrechungen ignoriert und es werden keine Ereignis ausgelöst.
   * Die Zeitleiste, die TVSDK der Player-Anwendung zur Verfügung stellt, wird auch dann nicht geändert, wenn Werbeunterbrechungen übersprungen werden.
   * Der aktuelle Zeitwert springt mit der Dauer der übersprungenen Werbeunterbrechung vorwärts (bei schnellem Vorwärts) oder rückwärts (bei schnellem Zurückspulen). Durch dieses Sprungverhalten für die aktuelle Zeit bleibt die Stream-Dauer während der Trick-Wiedergabe unverändert. Ihre Player-Anwendung kann den lokalen Zeitwert abrufen, um die Zeit relativ zum Hauptinhalt zu verfolgen. Für die Werte, die für die lokale Zeit zurückgegeben werden, wenn eine Anzeige übersprungen wird, werden keine Zeitsprünge ausgeführt.
   * Das `MediaPlayerEvent.AD_BREAK_SKIPPED` Ereignis wird unmittelbar vor dem Überspringen einer Werbeunterbrechung ausgelöst. Ihr Player kann dieses Ereignis verwenden, um benutzerdefinierte Logik in Bezug auf die übersprungenen Werbeunterbrechungen zu implementieren.
   * Beim Beenden der Trick-Wiedergabe werden dieselben Regeln für die Anzeigenwiedergabe aufgerufen wie beim Beenden der Suche.

      Wie bei der Suche hängt das Verhalten daher davon ab, ob sich die Wiedergaberichtlinie Ihrer Anwendung von der Standardrichtlinie unterscheidet. Die Standardeinstellung ist, dass die letzte übersprungene Werbeunterbrechung an dem Punkt wiedergegeben wird, an dem Sie aus dem Trick Play-Modus herauskommen.

