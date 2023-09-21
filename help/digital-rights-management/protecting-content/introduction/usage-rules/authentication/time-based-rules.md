---
title: Zeitbasierte Regeln
description: Zeitbasierte Regeln
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Zeitbasierte Regeln {#time-based-rules}

Primetime DRM verwendet die &quot;weiche Durchsetzung&quot;zeitbasierter Lizenzbeschränkungen. Wenn während der Wiedergabe eines Videos eine zeitliche Berechtigung abläuft, wird die Wiedergabe von Primetime DRM standardmäßig erst beim nächsten erneuten Erstellen des Video-Streams eingeschränkt (durch Aufruf von `Netstream.stop()` und `Netstream.play()`).

Während die weiche Durchsetzung das Standardverhalten ist, können Sie die harte Durchsetzung auch aktivieren, indem Sie eine der folgenden Aufgaben ausführen:

* Lassen Sie Ihren Videoplayer die Lizenz regelmäßig abfragen, um sicherzustellen, dass keine der Zeitbeschränkungen abgelaufen ist. Dies kann durch Aufrufen von `DRMManager.loadVoucher(LOCAL_ONLY).` Ein Fehlercode gibt an, dass die lokal gespeicherte Lizenz nicht mehr gültig ist.
* Wann immer der Benutzer klickt **[!UICONTROL Pause]**, können Sie den aktuellen Video-Zeitstempel aufzeichnen und dann `Netstream.stop()`. Wenn der Benutzer auf die Play -Schaltfläche klickt, können Sie zum aufgezeichneten Speicherort suchen und dann `Netstream.play()`.

## Startdatum {#start-date}

Das Startdatum gibt das Datum an, nach dem eine Lizenz gültig ist.

Anwendungsbeispiel: Verwenden Sie ein absolutes Datum, um Inhaltslizenzen vor dem Verfügbarkeitsdatum eines Assets zu erteilen oder eine &quot;Embargo&quot;-Periode zu erzwingen.

## Enddatum {#end-date}

Das Enddatum gibt das Datum an, nach dem eine Lizenz abläuft.

Anwendungsbeispiel: Verwenden Sie ein absolutes Ablaufdatum, um das Ende der Vertriebsrechte widerzuspiegeln.

## Relatives Enddatum {#relative-end-date}

Das relative Enddatum gibt das Ablaufdatum der Lizenz an, das in Bezug auf das Verpackungsdatum und nicht in Bezug auf das Datum der Lizenzerteilung angegeben wird.

Anwendungsbeispiel: Verwenden Sie in einem automatisierten Verpackungsprozess eine einzelne Primetime-DRM-Richtlinie mit dieser Option für eine Reihe von Videos, um das Ablaufdatum auf 30 Tage relativ zum Verpackungsdatum festzulegen.

## Lizenzzwischenspeicherungsdauer{#license-caching-duration}

Die Dauer der Lizenzzwischenspeicherung gibt an, wie lange eine Lizenz im lokalen Lizenzspeicher des Clients auf dem Datenträger zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Alternativ können Sie ein absolutes Datum und eine absolute Uhrzeit angeben, nach denen eine Lizenz nicht mehr zwischengespeichert werden kann.

Sobald das Ablaufdatum des Caches abgelaufen ist, ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Anwendungsbeispiel: Verwenden Sie die Lizenz-Caching-Dauer, um eine feste Zeitdauer für eine bestimmte Lizenz anzugeben, z. B. in einem Nutzungsszenario für die Anmietung. Sie können eine 30-tägige Vermietung (mit Lizenz-Caching) angeben, um die Gesamtlizenzdauer anzugeben, innerhalb der die Inhalte verbraucht werden sollen.

## Wiedergabefenster {#playback-window}

Das Wiedergabefenster gibt die Dauer an, für die eine Lizenz nach der ersten Verwendung zum Abspielen geschützter Inhalte gültig ist.

Anwendungsbeispiel: Bei einigen Geschäftsmodellen ist eine Mietzeit von 30 Tagen zulässig. Sobald die Wiedergabe beginnt, muss die Wiedergabe jedoch innerhalb von 48 Stunden abgeschlossen sein. In diesem Fall ist die 48-Stunden-Dauer der Lizenz das Wiedergabefenster.

**Ab Version 5.3** - Das Wiedergabefenster unterstützt auch die Option &quot;Hard Stopp&quot;aktivieren oder deaktivieren. Dies gibt an, ob der Entschlüsselungskontext für die Wiedergabe nach Ablauf des Wiedergabefensters angehalten (aktiviert) oder trotz Ablauf fortgesetzt (deaktiviert) werden soll.

>[!NOTE]
>
>Die Option &quot;hartes Anhalten&quot;funktioniert nicht ordnungsgemäß mit dem Wiedergabefenster, wenn sie zusammen mit diesem verwendet wird (das Wiedergabefenster wird nicht berücksichtigt). Die Wiedergabe von Inhalt im Wiedergabefenster ohne sicheres Anhalten entspricht der Beschränkung des Wiedergabefensters.
