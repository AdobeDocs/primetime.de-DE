---
description: Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht es, sich über eine Vielzahl von Failover-Versuchen wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.
seo-description: Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht es, sich über eine Vielzahl von Failover-Versuchen wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.
seo-title: Fehlendes Segmentfailover
title: Fehlendes Segmentfailover
uuid: 17ee1221-e1eb-4f64-a406-4d7eff1d7555
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Fehlendes Segmentfailover{#missing-segment-failover}

Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht es, sich über eine Vielzahl von Failover-Versuchen wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.

Wenn ein Segment auf dem Server fehlt, weil beispielsweise die Manifestdatei nicht vorhanden ist, das Segment nicht heruntergeladen werden kann usw., versucht TVSDK, einen Fehler zu beheben, indem folgende Optionen ausgeführt werden:

1. Versucht in einer Variantendatei ein Failover mit derselben Bitrate auf dasselbe Segment.
1. Wechseln Sie zu einer alternativen Bitrate (ABR Switch) in derselben Datei.
1. Durchlaufen Sie jede verfügbare Bitrate in jeder verfügbaren Variante.
1. Überspringen Sie das Segment und geben Sie eine Warnung aus.

Wenn TVSDK kein alternatives Segment abrufen kann, wird eine `CONTENT_ERROR` Fehlerbenachrichtigung ausgelöst. Diese Benachrichtigung enthält eine innere Benachrichtigung mit dem Code- `DOWNLOAD_ERROR` Code. Wenn der Stream mit dem Problem eine alternative Audiospur ist, wird die `AUDIO_TRACK_ERROR` Fehlerbenachrichtigung generiert.

Wenn die Video-Engine kontinuierlich keine Segmente abrufen kann, werden fortlaufende Segmente auf 5 übersprungen, danach wird die Wiedergabe gestoppt und ein `NATIVE_ERROR` mit Code 5 ausgegeben.

>[!NOTE]
>
>Die ABR-Steuerungsparameter (adaptive Bitrate) werden bei einem Failover nicht berücksichtigt. Der Grund dafür ist, dass der Failover-Mechanismus so konzipiert ist, dass alle derzeit verfügbaren Wiedergabelisten unabhängig von ihrem Bitrate-Profil als Backup-Streams verwendet werden können.
>
>Während eines Failover-Vorgangs kann es einen Profil-Switch geben. Tritt beim Herunterladen eines der Wiedergabelistensegmente ein Fehler auf, werden ABR-Steuerungsparameter wie die zulässige Min-/Max-Bitrate ignoriert.

