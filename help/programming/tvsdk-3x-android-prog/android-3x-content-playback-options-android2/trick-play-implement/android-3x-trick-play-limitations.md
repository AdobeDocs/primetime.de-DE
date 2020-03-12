---
description: 'null'
seo-description: 'null'
seo-title: Einschränkungen und Verhalten bei der Trick-Wiedergabe
title: Einschränkungen und Verhalten bei der Trick-Wiedergabe
uuid: c28cc8db-3f45-488e-ab72-b102b3a1fab2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Einschränkungen und Verhalten bei der Trick-Wiedergabe {#limitations-and-behavior-for-trick-play}

<!--<a id="section_2BC43539C5C142E085D06A7E35C76726"></a>-->

Einschränkungen für den Trick Play-Modus:

* Die Master-Playlist muss nur iFrame-Segmente enthalten.

   Auf dem Bildschirm werden nur die Schlüsselbilder aus der Iframe-Spur angezeigt.
* Die Audiospur und die Untertitel sind deaktiviert.
* Wiedergabe und Pause sind aktiviert.
* Sie können den Trick-Play-Modus in eine beliebige zulässige Wiedergabegeschwindigkeit (Wiedergabe oder Pause) beenden.
* Wenn Anzeigen in den Stream eingebunden werden:

   * Sie können nur zum Trick play gehen, während Sie den Hauptinhalt wiedergeben. Wenn Sie versuchen, während einer Werbeunterbrechung zu &quot;trick play&quot;zu wechseln, wird ein Fehler ausgelöst.
   * Nach dem Start des Trick Play-Modus werden Werbeunterbrechungen ignoriert und es werden keine Ereignis ausgelöst.
   * Die Zeitleiste, die TVSDK dem Player zur Verfügung stellt, wird auch dann nicht geändert, wenn Werbeunterbrechungen übersprungen werden.
   * Der aktuelle Zeitwert springt mit der Dauer der übersprungenen Werbeunterbrechung vorwärts (bei schnellem Vorwärts) oder rückwärts (bei schnellem Zurückspulen).

      Durch dieses Sprungverhalten für die aktuelle Zeit bleibt die Stream-Dauer während der Trick-Wiedergabe unverändert. Ihr Player kann die Zeit relativ zum Hauptinhalt verfolgen. Für die Werte, die für die lokale Zeit zurückgegeben werden, wenn eine Anzeige übersprungen wird, werden keine Zeitsprünge ausgeführt.
   * Das `MediaPlayerEvent.AD_BREAK_SKIPPED` Ereignis wird unmittelbar vor dem Überspringen einer Werbeunterbrechung ausgelöst.

      Ihr Player kann dieses Ereignis verwenden, um benutzerdefinierte Logik in Bezug auf die übersprungenen Werbeunterbrechungen zu implementieren.

   * Beim Beenden der Trick-Wiedergabe werden dieselben Regeln für die Anzeigenwiedergabe aufgerufen wie beim Beenden der Suche.

      Wie bei der Suche hängt das Verhalten davon ab, ob sich die Wiedergaberichtlinie der Anwendung von der Standardrichtlinie unterscheidet. Die Standardeinstellung ist, dass die letzte übersprungene Werbeunterbrechung an dem Punkt wiedergegeben wird, an dem Sie die Trick-Wiedergabe beendet haben.