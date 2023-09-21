---
description: Es gibt einige Einschränkungen und einige Probleme in der Art, wie sich der Trick Play-Modus verhält.
title: Einschränkungen und Verhalten bei der Trickwiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Einschränkungen und Verhalten bei der Trickwiedergabe{#limitations-and-behavior-for-trick-play}

Es gibt einige Einschränkungen und einige Probleme in der Art, wie sich der Trick Play-Modus verhält.

<!--<a id="section_8B88E281A0FA4661B4C2C70A0ABED57C"></a>-->

Hier finden Sie die Einschränkungen für den Trick Play-Modus:

* Die Master-Wiedergabeliste muss nur I-Frame-Segmente enthalten. Auf dem Bildschirm werden nur die Schlüsselrahmen der I-Frame-Spur angezeigt.
* Der Audio-Track und die Untertitel sind deaktiviert.
* Die Logik der adaptiven Bitrate (ABR) ist deaktiviert. TVSDK wählt eine Bitrate zwischen der niedrigsten bereitgestellten Rate und 800 Kbit/s aus und verwendet diese Rate während der gesamten Trick-Play-Sitzung.
* Wiedergabe und Pause sind aktiviert.
* Suche ist verboten. Um zu suchen, rufen Sie `pause` , um den Wiedergabemodus zu beenden, und rufen Sie dann `seek`.

* Sie können vom Trick-Play-Modus zu einer beliebigen zulässigen Wiedergaberate wechseln (Wiedergabe oder Pause).
* Wenn Anzeigen in den Stream integriert werden:

   * Sie können nur während der Wiedergabe des Hauptinhalts zum Trick Play gehen. Ein Fehler wird ausgelöst, wenn Sie versuchen, während einer Werbeunterbrechung zu &quot;trick play&quot;zu wechseln.
   * Nach dem Starten des Trick Play-Modus werden die Werbeunterbrechungen ignoriert und es werden keine Anzeigenereignisse ausgelöst.
   * Die Zeitleiste, die TVSDK der Player-Anwendung zur Verfügung stellt, wird auch dann nicht geändert, wenn Werbeunterbrechungen übersprungen werden.
   * Der aktuelle Zeitwert springt mit der Dauer der übersprungenen Werbeunterbrechung vorwärts (schnell vorwärts) oder rückwärts (bei schnellem Zurückspulen). Durch dieses Sprungverhalten für die aktuelle Zeit kann die Stream-Dauer während der Trick Play-Zeit unverändert bleiben. Ihre Player-Anwendung kann den lokalen Zeitwert abrufen, um die Zeit relativ zum Hauptinhalt zu verfolgen. Für die Werte, die beim Überspringen einer Anzeige für die lokale Zeit zurückgegeben werden, werden keine Zeitpunkte ausgeführt.
   * Die `MediaPlayerEvent.AD_BREAK_SKIPPED` -Ereignis unmittelbar bevor eine Werbeunterbrechung übersprungen wird. Ihr Player kann dieses Ereignis verwenden, um benutzerdefinierte Logik im Zusammenhang mit den übersprungenen Werbeunterbrechungen zu implementieren.
   * Beim Beenden der Suche wird dieselbe Richtlinie für die Anzeigenwiedergabe aufgerufen wie beim Beenden der Suche.

     Wie bei der Suche hängt das Verhalten daher davon ab, ob sich die Wiedergaberichtlinie Ihrer Anwendung von der standardmäßigen unterscheidet. Die Standardeinstellung ist, dass die letzte übersprungene Werbeunterbrechung an dem Punkt wiedergegeben wird, an dem Sie aus dem Trick Play-Modus kommen.
