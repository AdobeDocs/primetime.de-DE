---
title: Erleichtern Sie den HLS-Player beim Umschalten auf Failover-/Backup-Streams
description: Der Apple HLS-Stapel unterstützt das Wechseln zu Failover-/Backup-Streams, wenn keine Streams des primären Satzes abgerufen werden können. Für Apple HLS-Geräte können Sie zur Erleichterung des Failover den Manifestserver signalisieren, um in der Übergeordnet-Wiedergabeliste identifizierte Primär- und Failover-Streams als getrennte Sätze zu behandeln (mit eigenen UUIDs).
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# Erleichtern Sie den HLS-Player beim Umschalten auf Failover-/Backup-Streams {#facilitating-hls-player-switching-to-failover-backup-streams}

Der Apple HLS-Stapel unterstützt das Wechseln zu Failover-/Backup-Streams, wenn keine Streams des primären Satzes abgerufen werden können. Für Apple HLS-Geräte können Sie zur Erleichterung des Failover den Manifestserver signalisieren, um in der Übergeordnet-Wiedergabeliste identifizierte Primär- und Failover-Streams als getrennte Sätze zu behandeln (mit eigenen UUIDs).

Um den Umstieg auf Failover- oder Backup-Streams auf Apple HLS-Geräten zu erleichtern, können Sie den Parameter `ptfailover` in der Bootstrap-URL angeben. Wenn Sie diesen Parameter angeben, erstellt der Manifestserver für jeden Failover-Satz separate Wiedergabesitzungen (die die zugefügten Anzeigen bestimmen).

## Details

Vorgehensweise von SSAI beim Umschalten von HLS auf Failover/Backup, wenn `ptfailover=true` in die Bootstrap-Anforderung einbezogen wird:

* Wenn eine Übergeordnet-Playlist primäre und Sicherungssätze enthält:

   * Der Manifestserver identifiziert AV-Stream-URLs für verschiedene Failover-Sets mit dem Attribut `BANDWIDTH` und der Parsereihenfolge von AV-Stream-URLs. Sie erstellt separate interne Wiedergabesitzungen (durch separate UUIDs gekennzeichnet) und Stream-URLs, die auf Manifestserver verweisen, wobei die verschiedenen UUIDs verschiedene Wiedergabesitzungen identifizieren.
   * Der Manifestserver identifiziert I-Frame-Stream-URLs für verschiedene Failover-Sets mit dem übereinstimmenden Attribut `RESOLUTION` und der Parsereihenfolge der I-Frame-Stream-URLs. SSAI verwendet die UUIDs zur Identifizierung der zugehörigen AV-Streams für I-Frame-Stream-URLs, die auf SSAI verweisen.
   * Für diese Funktion unterstützt der Manifestserver nur `EXT-X-MEDIA`-Gruppen ohne URI-Attribute in der Übergeordnet-Wiedergabeliste.
   * Der Manifestserver erkennt eine 404-Fehlerantwort eines CDN mit einem `X-Object-Too-Old: true`-Header und behält den Statuscode und den Header bei, wenn diese Antwort an den Player gesendet wird.

* Pre-Roll-Anzeigen werden nur zum primären Satz hinzugefügt. Sie sind in den Failover-Sets vollständig deaktiviert, um falsche und/oder duplizierte Pre-Roll-Anzeigen zu vermeiden, wenn der Player zu Failover-Streams wechselt.
