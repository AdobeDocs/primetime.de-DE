---
title: Erleichtern des HLS-Players beim Wechseln zu Failover/Backup-Streams
description: Der Apple HLS-Stapel unterstützt das Wechseln zu Failover-/Backup-Streams, wenn keine Streams des Hauptsatzes abgerufen werden können. Bei Apple HLS-Geräten können Sie zur Erleichterung des Failover den Manifestserver dahingehend signalisieren, dass Primär- und Failover-Streams, die in der Master-Wiedergabeliste als getrennte Sets identifiziert werden (mit eigenen UUIDs), behandelt werden.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Erleichtern des HLS-Players beim Wechseln zu Failover/Backup-Streams {#facilitating-hls-player-switching-to-failover-backup-streams}

Der Apple HLS-Stapel unterstützt das Wechseln zu Failover-/Backup-Streams, wenn keine Streams des Hauptsatzes abgerufen werden können. Bei Apple HLS-Geräten können Sie zur Erleichterung des Failover den Manifestserver dahingehend signalisieren, dass Primär- und Failover-Streams, die in der Master-Wiedergabeliste als getrennte Sets identifiziert werden (mit eigenen UUIDs), behandelt werden.

Um den Wechsel zu Failover- oder Backup-Streams auf Apple HLS-Geräten zu erleichtern, können Sie die `ptfailover` in der Bootstrap-URL. Wenn Sie diesen Parameter angeben, erstellt der Manifestserver für jeden Failover-Satz separate Wiedergabesitzungen (die die zugewiesenen Anzeigen bestimmen).

## Details

So behandelt SSAI das Wechseln von HLS zu Failover/Backup, wenn Sie `ptfailover=true` in der Bootstrap-Anfrage:

* Wenn eine Master-Playlist Primär- und Sicherungssätze enthält:

   * Der Manifestserver identifiziert AV-Stream-URLs für verschiedene Failover-Sets mithilfe der `BANDWIDTH` -Attribut und die Parse-Reihenfolge der AV-Stream-URLs. Sie erstellt separate interne Wiedergabesitzungen (identifiziert durch separate UUIDs) und Stream-URLs, die auf Manifestserver verweisen, wobei die verschiedenen UUIDs verschiedene Wiedergabesitzungen identifizieren.
   * Der Manifestserver identifiziert I-Frame-Stream-URLs für verschiedene Failover-Sets mithilfe der übereinstimmenden `RESOLUTION` -Attribut und die Parse-Reihenfolge der I-Frame-Stream-URLs. SSAI verwendet die UUIDs zur Identifizierung der zugehörigen AV-Streams für I-Frame-Stream-URLs, die auf SSAI verweisen.
   * Für diese Funktion unterstützt der Manifestserver nur `EXT-X-MEDIA` Gruppen ohne URI-Attribute in der Master-Wiedergabeliste.
   * Der Manifestserver erkennt eine 404-Fehlerantwort von einem CDN mit einer `X-Object-Too-Old: true` und behält den Status-Code und die Kopfzeile beim Senden dieser Antwort an den Player bei.

* Pre-Roll-Anzeigen werden nur zur Hauptmenge hinzugefügt. Sie sind in den Failover-Sets vollständig deaktiviert, um fehlerhafte und/oder duplizierte Pre-Roll-Anzeigen zu vermeiden, wenn der Player zu Failover-Streams wechselt.
