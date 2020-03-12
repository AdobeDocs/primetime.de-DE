---
description: Der Apple HLS-Stapel unterstützt das Wechseln zu Failover-/Backup-Streams, wenn keine Streams des primären Satzes abgerufen werden können. Für Apple HLS-Geräte können Sie zur Erleichterung des Failover den Manifestserver signalisieren, um Primär- und Failover-Streams, die in der Master-Wiedergabeliste als getrennte Sätze (mit eigenen UUIDs) identifiziert werden, zu behandeln.
seo-description: Der Apple HLS-Stapel unterstützt das Wechseln zu Failover-/Backup-Streams, wenn keine Streams des primären Satzes abgerufen werden können. Für Apple HLS-Geräte können Sie zur Erleichterung des Failover den Manifestserver signalisieren, um Primär- und Failover-Streams, die in der Master-Wiedergabeliste als getrennte Sätze (mit eigenen UUIDs) identifiziert werden, zu behandeln.
seo-title: Erleichterung des Umstiegs des HLS-Players auf Failover-/Backup-Streams
title: Erleichterung des Umstiegs des HLS-Players auf Failover-/Backup-Streams
uuid: 2fea8a51-e4cb-4fc9-82d5-6305a1d96603
translation-type: tm+mt
source-git-commit: 6863b63c7fa0068c3c5060fb946515c6cc5e3bff

---


# Erleichterung des Umstiegs des HLS-Players auf Failover-/Backup-Streams {#facilitating-hls-player-switching-to-failover-backup-streams}

Der Apple HLS-Stapel unterstützt das Wechseln zu Failover-/Backup-Streams, wenn keine Streams des primären Satzes abgerufen werden können. Für Apple HLS-Geräte können Sie zur Erleichterung des Failover den Manifestserver signalisieren, um Primär- und Failover-Streams, die in der Master-Wiedergabeliste als getrennte Sätze (mit eigenen UUIDs) identifiziert werden, zu behandeln.

Um das Wechseln zu Failover- oder Backup-Streams auf Apple HLS-Geräten zu erleichtern, können Sie den `ptfailover` Parameter in der Bootstrap-URL angeben. Wenn Sie diesen Parameter angeben, erstellt der Manifestserver für jeden Failover-Satz separate Wiedergabesitzungen (die die zugefügten Anzeigen bestimmen).

## Details

Vorgehensweise von SSAI beim Umschalten von HLS auf Failover/Backup, wenn Sie `ptfailover=true` in die Bootstrap-Anforderung einbeziehen:

* Wenn eine Master-Playlist Primär- und Sicherungssätze enthält:

   * Der Manifestserver identifiziert AV-Stream-URLs für verschiedene Failover-Sätze anhand des `BANDWIDTH` Attributs und der Reihenfolge der Analyse von AV-Stream-URLs. Sie erstellt separate interne Wiedergabesitzungen (durch separate UUIDs gekennzeichnet) und Stream-URLs, die auf Manifestserver verweisen, wobei die verschiedenen UUIDs verschiedene Wiedergabesitzungen identifizieren.
   * Der Manifestserver identifiziert I-Frame-Stream-URLs für verschiedene Failover-Sätze anhand des übereinstimmenden `RESOLUTION` Attributs und der Reihenfolge der Analyse von I-Frame-Stream-URLs. SSAI verwendet die UUIDs zur Identifizierung der zugehörigen AV-Streams für I-Frame-Stream-URLs, die auf SSAI verweisen.
   * Für diese Funktion unterstützt der Manifestserver nur `EXT-X-MEDIA` Gruppen ohne URI-Attribute in der Master-Playlist.
   * Der Manifestserver erkennt eine 404-Fehlerantwort von einem CDN mit einem `X-Object-Too-Old: true` Header und behält den Statuscode und den Header bei, wenn diese Antwort an den Player gesendet wird.

* Pre-Roll-Anzeigen werden nur zum primären Satz hinzugefügt. Sie sind in den Failover-Sets vollständig deaktiviert, um falsche und/oder duplizierte Pre-Roll-Anzeigen zu vermeiden, wenn der Player zu Failover-Streams wechselt.

