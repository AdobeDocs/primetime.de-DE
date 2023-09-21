---
title: Zeitbasierte Regeln definieren
description: Zeitbasierte Regeln definieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Zeitbasierte Regeln definieren {#defining-time-based-rules}

Adobe Access verwendet die &quot;weiche Durchsetzung&quot;zeitbasierter Lizenzbeschränkungen. Wenn bei der Wiedergabe eines Videos eine zeitliche Berechtigung abläuft, wird die Wiedergabe standardmäßig erst beim nächsten erneuten Erstellen des Video-Streams durch Aufruf von `Netstream.stop()` und `Netstream.play()`).

Während die weiche Durchsetzung das Standardverhalten ist, können Sie die harte Durchsetzung auch aktivieren, indem Sie eine der folgenden Aufgaben ausführen:

* Lassen Sie Ihren Videoplayer die Lizenz regelmäßig abfragen, um sicherzustellen, dass keine der Zeitbeschränkungen abgelaufen ist. Dies kann durch Aufrufen von `DRMManager.loadVoucher(LOCAL_ONLY).`Ein Fehlercode gibt an, dass die lokal gespeicherte Lizenz nicht mehr gültig ist.
* Wenn der Benutzer auf die Schaltfläche &quot;Pause&quot;klickt, können Sie den aktuellen Video-Zeitstempel aufzeichnen und dann `Netstream.stop().`Wenn der Benutzer auf die Play -Schaltfläche klickt, können Sie zum aufgezeichneten Speicherort suchen und dann `Netstream.play()`.

## Startdatum {#start-date}

Gibt das Datum an, nach dem eine Lizenz gültig ist.

Anwendungsbeispiel: Verwenden Sie ein absolutes Datum, um Inhaltslizenzen vor dem Verfügbarkeitsdatum eines Assets zu erteilen oder eine &quot;Embargo&quot;-Periode zu erzwingen.

## Enddatum {#end-date}

Gibt das Datum an, nach dem eine Lizenz abläuft.

Anwendungsbeispiel: Verwenden Sie ein absolutes Ablaufdatum, um das Ende der Vertriebsrechte widerzuspiegeln.

## Relatives Enddatum {#relative-end-date}

Gibt das Ablaufdatum der Lizenz an, ausgedrückt als Verpackungsdatum.

Anwendungsbeispiel: Verwenden Sie in einem automatisierten Verpackungsprozess eine einzelne Richtlinie mit dieser Option für eine Reihe von Videos, um das Ablaufdatum auf 30 Tage relativ zum Verpackungsdatum festzulegen.

## Lizenzzwischenspeicherungsdauer {#license-caching-duration}

Gibt die Dauer an, für die eine Lizenz im lokalen Lizenzspeicher des Clients auf dem Datenträger zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Alternativ können Sie ein absolutes Datum/eine absolute Uhrzeit angeben, nach dem eine Lizenz nicht mehr zwischengespeichert werden kann.

Sobald das Ablaufdatum des Caches abgelaufen ist, ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Anwendungsbeispiel: Verwenden Sie die Lizenz-Caching-Dauer, um eine feste Zeitdauer für eine bestimmte Lizenz anzugeben, z. B. in einem Nutzungsszenario für die Anmietung. Es kann eine 30-tägige Vermietung (mit Lizenz-Caching) angegeben werden, um die Gesamtlizenzdauer anzugeben, innerhalb derer die Inhalte genutzt werden können.

## Wiedergabefenster {#playback-window}

Gibt die Dauer an, für die eine Lizenz nach der ersten Verwendung zum Abspielen geschützter Inhalte gültig ist.

Anwendungsbeispiel: Bei einigen Geschäftsmodellen ist eine Mietzeit von 30 Tagen zulässig. Sobald die Wiedergabe beginnt, muss sie jedoch innerhalb von 48 Stunden abgeschlossen sein. Diese 48-Stunden-Gültigkeitsdauer der Lizenz ist als Wiedergabefenster definiert.

## Anforderungen für die Synchronisierung {#requirements-for-synchronization}

Gibt die Häufigkeit an, mit der der Client seinen Status mit dem Server synchronisiert. Wenn dem Client eine Out-of-Band-Lizenz erteilt wurde (ohne dass ein Lizenzserver kontaktiert wird), können Nutzungsregeln festlegen, dass der Client Synchronisierungsmeldungen an den Server senden muss, um die sichere Zeit des Clients zu synchronisieren und den Clientstatus an den Server zu melden.

Das Synchronisierungsverhalten wird mithilfe der folgenden Parameter definiert:

* Start Interval - Gibt an, wie lange es nach der letzten erfolgreichen Synchronisation warten muss, um eine weitere Synchronisierungsanforderung zu starten.
* Hard Stopp Interval (optional). Die Wiedergabe verweigern, wenn innerhalb der angegebenen Zeit keine erfolgreiche Synchronisierung stattgefunden hat.
* Wahrscheinlichkeit der erzwungenen Synchronisierung (optional). Wahrscheinlichkeit, mit der der Client eine Synchronisierungsmeldung vor dem nächsten Startintervall senden soll.

>[!NOTE]
>
>Diese Nutzungsregel wird von Adobe Access-Clients ab Version 3.0 unterstützt. Das Verhalten bei älteren Clients hängt von der vom Lizenzserver unterstützten Mindestversion des Clients ab. Siehe [Minimale Client-Version](../../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).
