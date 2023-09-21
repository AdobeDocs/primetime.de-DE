---
title: Einschränkungen und Verhalten bei der Trickwiedergabe
description: Einschränkungen und Verhalten bei der Trickwiedergabe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Einschränkungen und Verhalten bei der Trickwiedergabe {#limitations-and-behavior-for-trick-play}

<!--<a id="section_2BC43539C5C142E085D06A7E35C76726"></a>-->

Einschränkungen für den Trick Play-Modus:

* Die Master-Wiedergabeliste muss nur Iframe-Segmente enthalten.

  Auf dem Bildschirm werden nur die Schlüsselrahmen der Iframe-Spur angezeigt.
* Der Audio-Track und die Untertitel sind deaktiviert.
* Wiedergabe und Pause sind aktiviert.
* Sie können den Trick-Play-Modus in eine beliebige zulässige Wiedergabegeschwindigkeit (Wiedergabe oder Pause) beenden.
* Wenn Anzeigen in den Stream integriert werden:

   * Sie können nur während der Wiedergabe des Hauptinhalts zum Trick Play gehen. Ein Fehler wird ausgelöst, wenn Sie versuchen, während einer Werbeunterbrechung zu &quot;trick play&quot;zu wechseln.
   * Nach dem Start des Trick Play-Modus werden die Werbeunterbrechungen ignoriert und es werden keine Anzeigenereignisse ausgelöst.
   * Die Zeitleiste, die TVSDK dem Player offenlegt, wird auch dann nicht geändert, wenn Werbeunterbrechungen übersprungen werden.
   * Der aktuelle Zeitwert springt mit der Dauer der übersprungenen Werbeunterbrechung vorwärts (schnell vorwärts) oder rückwärts (bei schnellem Zurückspulen).

     Durch dieses Sprungverhalten für die aktuelle Zeit kann die Stream-Dauer während der Trick Play-Zeit unverändert bleiben. Ihr Player kann die Zeit nur relativ zum Hauptinhalt verfolgen. Für die Werte, die beim Überspringen einer Anzeige für die lokale Zeit zurückgegeben werden, werden keine Zeitpunkte ausgeführt.
   * Die `MediaPlayerEvent.AD_BREAK_SKIPPED` -Ereignis unmittelbar bevor eine Werbeunterbrechung übersprungen wird.

     Ihr Player kann dieses Ereignis verwenden, um benutzerdefinierte Logik im Zusammenhang mit den übersprungenen Werbeunterbrechungen zu implementieren.

   * Beim Beenden der Suche wird dieselbe Richtlinie für die Anzeigenwiedergabe aufgerufen wie beim Beenden der Suche.

     Wie bei der Suche hängt das Verhalten davon ab, ob sich die Wiedergaberichtlinie Ihrer Anwendung vom Standard unterscheidet. Die Standardeinstellung ist, dass die letzte übersprungene Werbeunterbrechung an dem Punkt wiedergegeben wird, an dem Sie aus der Trickwiedergabe herausgekommen sind.
