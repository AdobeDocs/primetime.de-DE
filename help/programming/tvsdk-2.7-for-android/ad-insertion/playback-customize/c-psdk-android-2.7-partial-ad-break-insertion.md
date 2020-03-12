---
description: 'null'
seo-description: 'null'
seo-title: Einfügen von Werbeunterbrechungen
title: Einfügen von Werbeunterbrechungen
uuid: cc071c89-f813-419e-a2b2-4f6a9fdccd6a
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Einfügen von Werbeunterbrechungen {#partial-ad-break-insertion}

Sie können eine TV-ähnliche Erfahrung aktivieren, um mitten in einer Anzeige in Live-Streams mitmachen zu können. Mit der Funktion zum Umbruch einer partiellen Anzeige können Sie ein TV-ähnliches Erlebnis nachahmen, bei dem der Client einen Live-Stream innerhalb eines Midroll Beginn, der in diesem Midroll Beginn wird. Es ähnelt dem Wechsel zu einem TV-Kanal und die Werbespots laufen nahtlos.

Wenn sich ein Benutzer beispielsweise mitten in einer 90-Sekunden-Werbeunterbrechung (drei 30-Sekunden-Anzeigen) und 10 Sekunden nach der zweiten Anzeige (d. h. nach 40 Sekunden Werbeunterbrechung) anmeldet, passiert Folgendes:

* Die zweite Anzeige wird für die verbleibende Dauer (20 Sekunden) und die dritte Anzeige abgespielt.
* Anzeigentracker für die teilweise wiedergegebene Anzeige (die zweite Anzeige) werden nicht ausgelöst. Nur der Tracker für die dritte Anzeige wird ausgelöst.

Dieses Verhalten ist nicht standardmäßig aktiviert. Gehen Sie wie folgt vor, um diese Funktion in Ihrer App zu aktivieren:

1. Deaktivieren Sie die Live-Prerolls mit der Methode setEnableLivePreroll der AdvertisingMetadata-Klasse.

   ```
   advertisingMetadata.setLivePreroll(false)  
   advertisingMetadata.setPreroll(false)
   ```

1. Schalten Sie die Voreinstellung für Einfügen von Werbeunterbrechungen ein. Verwenden Sie die neue Methode setPartialAdBreakPref in der MediaPlayer-Oberfläche, um diese Funktion EIN zu aktivieren. Verwenden Sie die getPartialAdBreakPref-Methode, um den aktuellen Status dieser Voreinstellung zu ermitteln.

   ```
   MediaPlayer mediaPlayer = new MediaPlayer(getActivity().getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
   ```

