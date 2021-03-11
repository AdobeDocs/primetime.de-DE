---
title: Einfügen von Werbeunterbrechungen
description: Einfügen von Werbeunterbrechungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Einfügen von Werbeunterbrechungen {#partial-ad-break-insertion}

Sie können eine TV-ähnliche Erfahrung aktivieren, um mitten in einer Anzeige in Live-Streams mitmachen zu können. Mit der Funktion &quot;Werbeunterbrechung bei partieller Anzeige&quot;können Sie ein TV-ähnliches Erlebnis nachahmen, bei dem der Client einen Live-Stream innerhalb eines Midrolls Beginn, der in diesem Midroll Beginn wird. Es ähnelt dem Wechsel zu einem TV-Kanal und die Werbespots laufen nahtlos.

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

