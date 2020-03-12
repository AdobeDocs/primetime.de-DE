---
seo-title: Definieren zeitbasierter Regeln
title: Definieren zeitbasierter Regeln
uuid: 17c69869-ac81-4561-9fb6-b1c5c9c4006d
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Definieren zeitbasierter Regeln {#defining-time-based-rules}

Adobe Access verwendet die &quot;weiche Durchsetzung&quot;zeitbasierter Lizenzbeschränkungen. Wenn ein Zeitrecht während der Wiedergabe eines Videos abläuft, schränkt Adobe Access standardmäßig die Wiedergabe nicht ein, bis der Videostream zum nächsten Mal neu erstellt wird (durch Aufruf `Netstream.stop()` und `Netstream.play()`).

Während die weiche Durchsetzung das Standardverhalten ist, können Sie auch eine harte Durchsetzung aktivieren, indem Sie eine der folgenden Aufgaben ausführen:

* Lassen Sie Ihren Videoplayer regelmäßig die Lizenz abfragen, um sicherzustellen, dass keine der Zeitbeschränkungen abgelaufen ist. Dies kann durch Aufrufen `DRMManager.loadVoucher(LOCAL_ONLY).`eines Fehlercodes erreicht werden, der angibt, dass die lokal gespeicherte Lizenz nicht mehr gültig ist.
* Wenn der Benutzer auf die Schaltfläche &quot;Anhalten&quot;klickt, können Sie den aktuellen Video-Zeitstempel aufzeichnen und dann aufrufen, `Netstream.stop().`wenn der Benutzer auf die Schaltfläche &quot;Abspielen&quot;klickt, können Sie zum aufgezeichneten Speicherort suchen und dann aufrufen `Netstream.play()`.

## Beginn {#start-date}

Gibt das Datum an, nach dem eine Lizenz gültig ist.

Verwendungsbeispiel: Verwenden Sie ein absolutes Datum, um Lizenzen für Inhalte vor dem Verfügbarkeitsdatum eines Assets auszustellen oder eine Sperrfrist durchzusetzen.

## Enddatum {#end-date}

Gibt das Datum an, nach dem eine Lizenz abläuft.

Verwendungsbeispiel: Verwenden Sie ein absolutes Ablaufdatum, um das Ende der Distributionsrechte widerzuspiegeln.

## Relatives Enddatum {#relative-end-date}

Gibt das Ablaufdatum der Lizenz in Relation zum Verpackungsdatum an.

Verwendungsbeispiel: Verwenden Sie in einem automatisierten Verpackungsprozess eine einzelne Richtlinie mit dieser Option für eine Reihe von Videos, um das Ablaufdatum auf 30 Tage bezogen auf das Verpackungsdatum festzulegen.

## Dauer der Lizenzzwischenspeicherung {#license-caching-duration}

Gibt an, wie lange eine Lizenz im lokalen Lizenzspeicher des Clients zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Sie können auch ein absolutes Datum/eine Uhrzeit angeben, nach dem eine Lizenz nicht mehr zwischengespeichert werden kann.

Nach Ablauf des Cache-Ablaufdatums ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Verwendungsbeispiel: Verwenden Sie die Lizenzzwischenspeicherungsdauer, um eine feste Zeitdauer für eine bestimmte Lizenz anzugeben, z. B. im Fall einer Vermietung. Eine 30-tägige Vermietung kann angegeben werden (mit Lizenz-Caching), um die gesamte Lizenzdauer anzugeben, innerhalb derer die Inhalte genutzt werden sollen.

## Wiedergabefenster {#playback-window}

Gibt an, wie lange eine Lizenz gültig ist, nachdem sie zum ersten Mal zum Abspielen geschützter Inhalte verwendet wird.

Verwendungsbeispiel: Bei einigen Geschäftsmodellen ist eine Vermietungszeit von 30 Tagen zulässig, die Wiedergabe muss jedoch innerhalb von 48 Stunden abgeschlossen sein. Diese 48-Stunden-Gültigkeitsdauer der Lizenz wird als Wiedergabefenster definiert.

## Anforderungen für die Synchronisierung {#requirements-for-synchronization}

Gibt die Häufigkeit an, mit der der Client seinen Status mit dem Server synchronisiert. Wenn dem Client eine Out-of-Band-Lizenz erteilt wurde (ohne dass ein Lizenzserver kontaktiert wird), können Nutzungsregeln festlegen, dass der Client Synchronisierungsmeldungen an den Server senden muss, um die sichere Zeit des Clients zu synchronisieren und den Clientstatus mit dem Server zu melden.

Das Synchronisierungsverhalten wird mithilfe der folgenden Parameter definiert:

* Beginn-Intervall — Gibt an, wie lange nach der letzten erfolgreichen Synchronisierung gewartet wird, bis eine weitere Synchronisierungsanforderung Beginn wird.
* Hartes Stoppintervall — (Optional). Die Wiedergabe ist nicht zulässig, wenn innerhalb der angegebenen Zeitspanne keine erfolgreiche Synchronisierung stattgefunden hat.
* Synchronisierungswahrscheinlichkeit erzwingen — (Optional). Möglichkeit, mit der der Client vor dem nächsten Beginn eine Synchronisierungsmeldung senden soll.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Diese Nutzungsregel wird von Adobe Access-Clients ab Version 3.0 unterstützt. Das Verhalten älterer Clients hängt von der vom Lizenzserver unterstützten Clientversion ab. Siehe [Minimum Client Version](../../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).