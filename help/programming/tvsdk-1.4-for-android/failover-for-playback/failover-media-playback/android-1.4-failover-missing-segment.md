---
description: Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht dies durch eine Vielzahl von Failover-Versuchen, wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.
title: Fehlendes Segment-Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Fehlendes Segment-Failover{#missing-segment-failover}

Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht dies durch eine Vielzahl von Failover-Versuchen, wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.

Wenn ein Segment auf dem Server fehlt, weil z. B. die Manifestdatei nicht vorhanden ist, das Segment nicht heruntergeladen werden kann usw. versucht TVSDK, einen Fehler zu beheben, indem folgende Optionen verwendet werden:

1. Versuchen Sie, in einer Variantendatei ein Failover für dasselbe Segment mit derselben Bitrate durchzuführen.
1. Wechseln Sie in derselben Datei zu einer alternativen Bitrate (ABR-Switch).
1. Durchlaufen Sie jede verfügbare Bitrate in jeder verfügbaren Variante.
1. Überspringen Sie das Segment und geben Sie eine Warnung aus.

Wenn TVSDK kein alternatives Segment abrufen kann, wird eine `CONTENT_ERROR` Fehlerbenachrichtigung. Diese Benachrichtigung enthält eine innere Benachrichtigung mit dem Code `DOWNLOAD_ERROR` Code. Wenn der Stream mit dem Problem ein alternativer Audio-Track ist, generiert die `AUDIO_TRACK_ERROR` Fehlerbenachrichtigung.

Wenn die Video-Engine kontinuierlich keine Segmente abrufen kann, werden kontinuierliche Segmente auf 5 übersprungen. Danach wird die Wiedergabe gestoppt und es wird ein Fehler bei der `NATIVE_ERROR` mit dem Code 5.

>[!NOTE]
>
>Die ABR-Steuerungsparameter (Adaptive Bitrate) werden bei einem Failover nicht berücksichtigt. Der Grund dafür ist, dass der Failover-Mechanismus so konzipiert ist, dass eine der derzeit verfügbaren Wiedergabelisten unabhängig von ihrem Bitratenprofil als Backup-Streams verwendet wird.
>
>Während eines Failover-Vorgangs kann es einen Profilwechsel geben. Wenn beim Herunterladen eines der Wiedergabelistensegmente ein Fehler auftritt, werden ABR-Steuerungsparameter wie die erlaubte Min-/Max-Bitrate ignoriert.
