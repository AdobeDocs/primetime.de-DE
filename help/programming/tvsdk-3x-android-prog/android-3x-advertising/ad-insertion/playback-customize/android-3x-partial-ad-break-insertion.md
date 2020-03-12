---
description: 'null'
seo-description: 'null'
seo-title: Einfügen von Werbeunterbrechungen
title: Einfügen von Werbeunterbrechungen
uuid: a81295b8-77fe-4475-a472-080ee7804d7a
translation-type: tm+mt
source-git-commit: fe9d7d1b2b23a70eb4e212de3d9bda47fc11d8f1

---


# Einfügen von Werbeunterbrechungen {#partial-ad-break-insertion}

Sie können eine TV-ähnliche Erfahrung aktivieren, um mitten in einer Anzeige in Live-Streams mitmachen zu können. Mit der Funktion zum Umbruch einer partiellen Anzeige können Sie ein TV-ähnliches Erlebnis nachahmen, bei dem der Client einen Live-Stream innerhalb eines Midroll Beginn, der in diesem Midroll Beginn wird. Es ähnelt dem Wechsel zu einem TV-Kanal und die Werbespots laufen nahtlos.

Wenn sich ein Benutzer beispielsweise mitten in einer 90-Sekunden-Werbeunterbrechung (drei 30-Sekunden-Anzeigen) und 10 Sekunden nach der zweiten Anzeige (d. h. nach 40 Sekunden Werbeunterbrechung) anmeldet, passiert Folgendes:

* Die zweite Anzeige wird für die verbleibende Dauer (20 Sekunden) und die dritte Anzeige abgespielt.
* Anzeigentracker für die teilweise wiedergegebene Anzeige (die zweite Anzeige) werden nicht ausgelöst. Nur der Tracker für die dritte Anzeige wird ausgelöst.

Dieses Verhalten ist nicht standardmäßig aktiviert. Gehen Sie wie folgt vor, um diese Funktion in Ihrer App zu aktivieren:

Schalten Sie die Voreinstellung für Einfügen von Werbeunterbrechungen ein. Verwenden Sie die neue Methode `setPartialAdBreakPref` in der MediaPlayer-Oberfläche, um diese Funktion EIN zu aktivieren. Verwenden Sie die `getPartialAdBreakPref` Methode, um den aktuellen Status dieser Voreinstellung zu ermitteln.

```
    MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
```

Die Pre-Roll-Anzeige wird, sofern verfügbar, abgespielt und dann vom Live-Point aus wiedergegeben, der dem Erlebnis des Live-Fernsehens nachbildet.
