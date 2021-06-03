---
title: Versionshinweise zu PTAI 21.5.1
description: Die PTAI-Versionshinweise beschreiben, was neu oder geändert ist, welche gelösten und bekannten Probleme im Primetime-Ad Insertion im Jahr 2021 aufgetreten sind.
exl-id: 39a05f6d-431a-4416-81b1-21d82c0dbd69
source-git-commit: fe0f5f3399d2e2ab3e07713fbcd29ede47888d98
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Primetime Ad Insertion 21.5.1 - Versionshinweise

Die Primetime-Ad Insertion-Versionshinweise 21.x.x beschreiben, was neu ist oder geändert wurde, Probleme gelöst wurden und bekannte Probleme in Primetime Ad Insertion im Jahr 2021.

## Neue Funktionen in PTAI 21.5.1

Wenn:  Mittwoch, 26. Mai 2021 von 3:30 Uhr bis 06:30 Uhr Ostzeit

* Unterstützung für veralteten Segmentierungstyp 0x01 (UPID) für SCTE-basierte Cue-Formate hinzugefügt.

* Neue Telemetrie für bevorstehende Dashboard-Änderungen hinzugefügt.

## Verbesserungen und Fehlerbehebungen in früheren Versionen

### Version 21.4.1

**Wann:** Donnerstag, 22. April 2021 von 2:00 Uhr bis 5:00 Uhr Ostzeit

**Änderungen**

* Die Beschränkung von Sitzungsanfragen wird aktiviert, um vor möglichen DDOS-Angriffen zu schützen. Sitzungen sind auf 10 Anforderungen pro Sekunde beschränkt, wobei die maximale Anzahl von 100 Anforderungen in der Warteschlange beträgt. Wir erwarten keine Auswirkungen auf Player, die sich gemäß HLS/DASH-Spezifikationen verhalten.

* Weitere Wartungs- und Sicherheitsverbesserungen

### Version 21.2.2

**Wann:** Dienstag, 23. Februar 2021 von 1:00 Uhr bis 04:00 Uhr Ostzeit

**Änderungen**

* Unterstützung für EXT-X-IMAGE-STREAM-INF-Stream-Einfügung/-Synchronisation in HLS-Streams hinzugefügt. Die Funktion wird über eine serverseitige Konfiguration aktiviert. Wenden Sie sich an Ihren technischen Kundenbetreuer, um die Funktion zu aktivieren.

### Version 21.2.1

**Wann:** Mittwoch, 3. Februar 2021 von 1:00 Uhr bis 04:00 Uhr Ostzeit

**Änderungen**

* Unterstützung für die DASH-Ausgabeoptimierung hinzugefügt: zeitbasierte Knotenkonsolidierung.

### Version 21.1.2

**Wann:** Dienstag, 19. Januar 2021 von 12:30 Uhr bis 08:30 Uhr Ostzeit

**Änderungen**

* Wartungsupdate: Aktualisierung von Primetime Ad Insertion-Backend-Memcache-Clustern.

### Version 21.1.1

**Wann:** Mittwoch, 13. Januar 2021 von 01:00 Uhr bis 04:00 Uhr Ostzeit

**Änderungen**

* Unterstützung für Affiliate-Verfügungen für SCTE35-basierte Cue-Formate hinzugefügt.
