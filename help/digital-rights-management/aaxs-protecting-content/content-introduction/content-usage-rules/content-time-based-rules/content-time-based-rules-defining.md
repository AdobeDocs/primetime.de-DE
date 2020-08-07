---
seo-title: Definieren zeitbasierter Regeln
title: Defining time-based rules
uuid: 17c69869-ac81-4561-9fb6-b1c5c9c4006d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---


# Definieren zeitbasierter Regeln {#defining-time-based-rules}

Adobe Access verwendet eine &quot;weiche Durchsetzung&quot;zeitbasierter Lizenzbeschränkungen. If a time right expires during playback of a video, the default behaviour of Adobe Access is to not restrict playback until the next time the video stream is recreated (by calling `Netstream.stop()` and `Netstream.play()`).

Während die weiche Durchsetzung das Standardverhalten ist, können Sie auch eine harte Durchsetzung aktivieren, indem Sie eine der folgenden Aufgaben ausführen:

* Lassen Sie Ihren Videoplayer regelmäßig die Lizenz abfragen, um sicherzustellen, dass keine der Zeitbeschränkungen abgelaufen ist. Dies kann durch Aufrufen `DRMManager.loadVoucher(LOCAL_ONLY).`eines Fehlercodes erreicht werden, der angibt, dass die lokal gespeicherte Lizenz nicht mehr gültig ist.
* Wenn der Benutzer auf die Schaltfläche &quot;Anhalten&quot;klickt, können Sie den aktuellen Video-Zeitstempel aufzeichnen und dann aufrufen, `Netstream.stop().`wenn der Benutzer auf die Schaltfläche &quot;Abspielen&quot;klickt, können Sie zum aufgezeichneten Speicherort suchen und dann aufrufen `Netstream.play()`.

## Beginn {#start-date}

Specifies the date after which a license is valid.

Example use case: Use an absolute date to issue content licenses ahead of the availability date of an asset, or to enforce an &quot;embargo&quot; period.

## End date {#end-date}

Specifies the date after which a licenses expires.

Example use case: Use an absolute expiration date to reflect the end of distribution rights.

## Relatives Enddatum {#relative-end-date}

Gibt das Ablaufdatum der Lizenz in Relation zum Verpackungsdatum an.

Verwendungsbeispiel: Verwenden Sie in einem automatisierten Verpackungsprozess eine einzelne Richtlinie mit dieser Option für eine Reihe von Videos, um das Ablaufdatum auf 30 Tage bezogen auf das Verpackungsdatum festzulegen.

## Dauer der Lizenzzwischenspeicherung {#license-caching-duration}

Gibt an, wie lange eine Lizenz im lokalen Lizenzspeicher des Clients zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Sie können auch ein absolutes Datum/eine Uhrzeit angeben, nach dem eine Lizenz nicht mehr zwischengespeichert werden kann.

Nach Ablauf des Cache-Ablaufdatums ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Verwendungsbeispiel: Verwenden Sie die Lizenzzwischenspeicherungsdauer, um eine feste Zeitdauer anzugeben, die für eine bestimmte Lizenz gültig ist, z. B. im Fall einer Vermietung. Eine 30-tägige Vermietung kann angegeben werden (mit Lizenz-Caching), um die gesamte Lizenzdauer anzugeben, innerhalb derer die Inhalte genutzt werden sollen.

## Wiedergabefenster {#playback-window}

Gibt an, wie lange eine Lizenz gültig ist, nachdem sie zum ersten Mal zum Abspielen geschützter Inhalte verwendet wird.

Verwendungsbeispiel: Bei einigen Geschäftsmodellen ist eine Vermietungszeit von 30 Tagen zulässig, die Wiedergabe muss jedoch innerhalb von 48 Stunden abgeschlossen sein. Diese 48-Stunden-Gültigkeitsdauer der Lizenz wird als Wiedergabefenster definiert.

## Anforderungen für die Synchronisierung {#requirements-for-synchronization}

Specifies the frequency in which the client will synchronize its state with the server. Wenn dem Client eine Out-of-Band-Lizenz erteilt wurde (ohne dass ein Lizenzserver kontaktiert wird), können Nutzungsregeln festlegen, dass der Client Synchronisierungsmeldungen an den Server senden muss, um die sichere Zeit des Clients zu synchronisieren und den Clientstatus mit dem Server zu melden.

The synchronization behavior is defined using the following parameters:

* Beginn-Intervall — Gibt an, wie lange nach der letzten erfolgreichen Synchronisierung gewartet wird, bis eine weitere Synchronisierungsanforderung Beginn wird.
* Hartes Stoppintervall — (Optional). Die Wiedergabe ist nicht zulässig, wenn innerhalb der angegebenen Zeitspanne keine erfolgreiche Synchronisierung stattgefunden hat.
* Force Sync Probability — (Optional). Probability with which the client should send a synchronize message before the next start interval.

>[!NOTE]
>
>This usage rule is supported by Adobe Access clients version 3.0 and higher. The behavior on older clients depends on the minimum client version supported by the license server. See, [Minimum Client Version](../../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).