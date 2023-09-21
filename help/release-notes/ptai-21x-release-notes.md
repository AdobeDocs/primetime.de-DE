---
title: Versionshinweise zu PTAI 21.11.1
description: Die PTAI-Versionshinweise beschreiben, was neu oder geändert ist, welche gelösten und bekannten Probleme im Primetime-Ad Insertion im Jahr 2021 aufgetreten sind.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Primetime Ad Insertion 21.11.1 - Versionshinweise

Die Primetime-Ad Insertion-Versionshinweise 21.xx.x beschreiben, was neu ist oder geändert wurde, Probleme gelöst wurden und bekannte Probleme in Primetime Ad Insertion im Jahr 2021.

## Neue Funktionen in PTAI 21.11.1

Wann: Dienstag, 9. November 2021 von 1:30 Uhr bis 04:30 Uhr Ostzeit

* [!UICONTROL EXT-X-IMAGE-STREAM-INF] ist jetzt pro Zone konfigurierbar.

* Roku Trick Play wird vollständig unterstützt.

## Verbesserungen und Fehlerbehebungen in früheren Versionen

### Version 21.10.1

Wann: Dienstag, 12. Oktober 2021 von 7:45 Uhr bis 13:45 Uhr Ostzeit

* Konsolidierte Server, produktionsfremde und nicht nützliche Server wurden entfernt.

### Primetime Ad Insertion Maintenance Release

Wann: Dienstag, 28. September 2021, von 5:00 Uhr bis 6:00 Uhr Ostzeit

* Aktualisierungen des Lastenausgleichs vom Elastic Load Balancer von AWS zum AWS Application Load Balancer, um die Funktionalität und Skalierbarkeit zu verbessern. Diese Lastenausgleichsmodule werden verwendet, um den Datenverkehr von der Ad Insertion-Ebene (SSAI/CSAI) zum Auditude-Backend zu leiten.

### Version 21.9.1

Wann: Dienstag, 7. September 2021 von 02:30 Uhr bis 05:30 Uhr Ostzeit

* Aktualisierungen der Infrastrukturkomponenten hinter den Mediations- und Reporting-Komponenten von Primetime Ad Insertion (Primetime Ads GUI).

### Version 21.8.1

Wann: Dienstag, 24. August 2021 von 2:00 Uhr bis 05:00 Uhr Ostzeit

* Unterstützung für DASH Live-/Linear-Streams hinzugefügt (VOD wird bereits unterstützt).

### Version 21.5.1

Wann: Mittwoch, 26. Mai 2021 von 3:30 Uhr bis 06:30 Uhr Ostzeit

**Änderungen**

* Unterstützung für veralteten Segmentierungstyp 0x01 (UPID) für SCTE-basierte Cue-Formate hinzugefügt.

* Neue Telemetrie für bevorstehende Dashboard-Änderungen hinzugefügt.

### Version 21.4.1

**Wenn:** Donnerstag, 22. April 2021 von 2:00 Uhr bis 5:00 Uhr Ostzeit

**Änderungen**

* Die Beschränkung von Sitzungsanfragen wird aktiviert, um vor möglichen DDOS-Angriffen zu schützen. Sitzungen sind auf 10 Anforderungen pro Sekunde beschränkt, wobei die maximale Anzahl von 100 Anforderungen in der Warteschlange beträgt. Wir erwarten keine Auswirkungen auf Player, die sich gemäß HLS/DASH-Spezifikationen verhalten.

* Weitere Wartungs- und Sicherheitsverbesserungen

### Version 21.2.2

**Wenn:** Dienstag, 23. Februar 2021 von 1:00 Uhr bis 04:00 Uhr Ostzeit

**Änderungen**

* Unterstützung für EXT-X-IMAGE-STREAM-INF-Stream-Einfügung/-Synchronisation in HLS-Streams hinzugefügt. Die Funktion wird über eine serverseitige Konfiguration aktiviert. Wenden Sie sich an Ihren technischen Kundenbetreuer, um die Funktion zu aktivieren.

### Version 21.2.1

**Wenn:** Mittwoch, 3. Februar 2021 von 1:00 Uhr bis 04:00 Uhr Ostzeit

**Änderungen**

* Unterstützung für DASH-Ausgabeoptimierung hinzugefügt: zeitbasierte Knotenkonsolidierung

### Version 21.1.2

**Wenn:** Dienstag, 19. Januar 2021 von 12:30 Uhr bis 08:30 Uhr Ostzeit

**Änderungen**

* Wartungsupdate: Aktualisierung von Primetime Ad Insertion-Backend-Memcache-Clustern.

### Version 21.1.1

**Wenn:** Mittwoch, 13. Januar 2021 von 01:00 Uhr bis 04:00 Uhr Ostzeit

**Änderungen**

* Unterstützung für Affiliate-Verfügungen für SCTE35-basierte Cue-Formate hinzugefügt.
