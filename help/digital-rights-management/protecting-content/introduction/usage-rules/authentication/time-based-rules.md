---
seo-title: Zeitbasierte Regeln
title: Zeitbasierte Regeln
uuid: 19a6ee7e-9580-48bb-a3a6-ff2cedcc796a
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Zeitbasierte Regeln {#time-based-rules}

Primetime DRM verwendet die &quot;weiche Durchsetzung&quot;zeitbasierter Lizenzbeschränkungen. Wenn ein Zeitrecht während der Wiedergabe eines Videos abläuft, schränkt Primetime DRM standardmäßig die Wiedergabe nicht ein, bis der Videostream zum nächsten Mal neu erstellt wird (durch Aufruf `Netstream.stop()` und `Netstream.play()`).

Während die weiche Durchsetzung das Standardverhalten ist, können Sie auch eine harte Durchsetzung aktivieren, indem Sie eine der folgenden Aufgaben ausführen:

* Lassen Sie Ihren Videoplayer regelmäßig die Lizenz abfragen, um sicherzustellen, dass keine der Zeitbeschränkungen abgelaufen ist. Dies kann durch Aufruf `DRMManager.loadVoucher(LOCAL_ONLY).` eines Fehlercodes erreicht werden, der angibt, dass die lokal gespeicherte Lizenz nicht mehr gültig ist.
* Wenn der Benutzer klickt, können Sie **[!UICONTROL Pause]** den aktuellen Video-Zeitstempel aufzeichnen und dann aufrufen `Netstream.stop()`. Wenn der Benutzer auf die Schaltfläche &quot;Abspielen&quot;klickt, können Sie zum aufgezeichneten Speicherort suchen und dann anrufen `Netstream.play()`.

## Beginn {#start-date}

Das Datum des Beginns gibt das Datum an, nach dem eine Lizenz gültig ist.

Verwendungsbeispiel: Verwenden Sie ein absolutes Datum, um Lizenzen für Inhalte vor dem Verfügbarkeitsdatum eines Assets auszustellen oder eine Sperrfrist durchzusetzen.

## Enddatum {#end-date}

Das Enddatum gibt das Datum an, nach dem eine Lizenz abläuft.

Verwendungsbeispiel: Verwenden Sie ein absolutes Ablaufdatum, um das Ende der Distributionsrechte widerzuspiegeln.

## Relatives Enddatum {#relative-end-date}

Das relative Enddatum gibt das Ablaufdatum der Lizenz an, das in Relation zum Verpackungsdatum und nicht zum Zeitpunkt der Erteilung der Lizenz angegeben wird.

Verwendungsbeispiel: Verwenden Sie in einem automatisierten Verpackungsprozess eine einzelne Primetime-DRM-Richtlinie mit dieser Option für eine Reihe von Videos, um das Ablaufdatum auf 30 Tage bezogen auf das Verpackungsdatum festzulegen.

## Dauer der Lizenzzwischenspeicherung{#license-caching-duration}

Die Dauer der Lizenzzwischenspeicherung gibt an, wie lange eine Lizenz im lokalen Lizenzspeicher des Clients zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Alternativ können Sie ein absolutes Datum und eine Uhrzeit angeben, nach denen eine Lizenz nicht mehr zwischengespeichert werden kann.

Nach Ablauf des Cache-Ablaufdatums ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Verwendungsbeispiel: Verwenden Sie die Lizenzzwischenspeicherungsdauer, um eine feste Zeitdauer für eine bestimmte Lizenz anzugeben, z. B. im Fall einer Vermietung. Sie können eine 30-Tage-Vermietung (mit Lizenz-Caching) angeben, um die gesamte Lizenzdauer anzugeben, innerhalb derer der Inhalt genutzt werden soll.

## Wiedergabefenster {#playback-window}

Im Wiedergabefenster wird die Dauer angegeben, die eine Lizenz nach der ersten Wiedergabe von geschütztem Inhalt gültig ist.

Verwendungsbeispiel: Bei einigen Geschäftsmodellen ist eine Mietdauer von 30 Tagen zulässig, aber nach dem Start der Wiedergabe muss die Wiedergabe innerhalb von 48 Stunden abgeschlossen sein. In diesem Fall ist die 48-Stunden-Dauer der Lizenz das Wiedergabefenster.

**Ab Version 5.3 vorwärts** - Das Wiedergabefenster unterstützt auch die Option &quot;Hard Stopp&quot;aktivieren oder deaktivieren. Dies gibt an, ob der Entschlüsselungskontext für die Wiedergabe nach Ablauf des Wiedergabefensters (aktiviert) oder trotz Ablauf (deaktiviert) fortgesetzt werden soll.

>[!NOTE]
>
>Die Option &quot;Stopp&quot;funktioniert nicht ordnungsgemäß mit dem Wiedergabefenster, wenn sie zusammen mit diesem verwendet wird (das Wiedergabefenster wird nicht berücksichtigt). Beim Abspielen von Inhalt mit dem Wiedergabefenster ohne sicheren Stopp wird die Beschränkung des Wiedergabefensters berücksichtigt.