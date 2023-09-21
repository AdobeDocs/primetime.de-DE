---
title: Teilweise Einfügen einer Werbeunterbrechung
description: Teilweise Einfügen einer Werbeunterbrechung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Teilweise Einfügen einer Werbeunterbrechung {#partial-ad-break-insertion}

Sie können ein TV-ähnliches Erlebnis aktivieren, um mitten in einer Anzeige in Live-Streams mitmachen zu können. Mit der Funktion für Teilanzeigen-Werbeunterbrechungen können Sie ein TV-ähnliches Erlebnis nachahmen, bei dem der Client einen Live-Stream innerhalb eines Midroll startet, dieser in diesem Midroll beginnt. Es ähnelt dem Wechsel zu einem Fernsehkanal und die Werbung läuft nahtlos.

Wenn ein Benutzer beispielsweise mitten in einer 90-Sekunden-Werbeunterbrechung (drei 30-Sekunden-Anzeigen) und 10 Sekunden nach der zweiten Anzeige (d. h. nach 40 Sekunden Werbeunterbrechung) Mitglied wird, passiert Folgendes:

* Die zweite Anzeige wird für die verbleibende Dauer (20 Sek.) gefolgt von der dritten Anzeige wiedergegeben.
* Anzeigentracker für die teilweise wiedergegebene Anzeige (die zweite Anzeige) werden nicht ausgelöst. Nur der Tracker für die dritte Anzeige wird ausgelöst.

Dieses Verhalten ist standardmäßig nicht aktiviert. Gehen Sie wie folgt vor, um diese Funktion in Ihrer App zu aktivieren:

Schalten Sie die Voreinstellung für &quot;Teil-Werbeunterbrechung einfügen&quot;ein. Neue Methode verwenden `setPartialAdBreakPref` in der MediaPlayer-Benutzeroberfläche, um diese Funktion EIN-/auszuschalten. Verwendung `getPartialAdBreakPref` -Methode, um den aktuellen Status dieser Voreinstellung zu ermitteln.

```
    MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
```

Die Pre-Roll-Anzeige wird wiedergegeben, sofern verfügbar, und dann wird der Inhalt ab dem Live-Point wiedergegeben, der das Erlebnis des Live-Fernsehens emuliert.
