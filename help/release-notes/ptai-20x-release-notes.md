---
title: PTAI 20.5.1 - Versionshinweise
description: Die Versionshinweise zu PTAI 20.5.1 beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme bei der Primetime Dynamic Ad Insertion im Jahr 2020.
translation-type: tm+mt
source-git-commit: 266b884707e9160d539a06fd089732ef8ade21ba
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Primetime Dynamic Ad Insertion 20.5.1 - Versionshinweise

Versionshinweise zur dynamischen Anzeigeneinfügung 20.5.1 beschreiben, was neu oder geändert ist, gelöste Probleme und bekannte Probleme bei der Primetime-Einfügen dynamischer Anzeigen im Jahr 2020.

## Neue Funktionen in PTAI 20.5.1

**Wenn:** Dienstag, 5. Mai 2020 von 04:00 Uhr bis 05:00 Uhr OST

* Es wurde ein Fehler behoben, der sicherstellte, dass beim Senden von if-Modified-Since-Headern korrekte CORS-Header bereitgestellt werden.

* Fehlerbehebungen im CRS-Dashboard.

* Aktualisierungen der Wartung.

## Änderungen in früheren Versionen

### Version 20.3.4

**Wenn:** Mittwoch, 1. April 2020 von 03:00 Uhr bis 04:00 Uhr OST

* Es wurde ein Fehler behoben, der dazu führte, dass Untertitel nach dem Einfügen der Anzeige in VOD/WebVTT nicht mehr synchronisiert wurden.

* Sicherheitsaktualisierungen.

### Version 20.3.3

**Wenn:** Donnerstag, 26. März 2020 von 03:00 Uhr bis 04:00 Uhr OST

* SSAI 4XX- und 5XX-Antworten liefern nun korrekt CORS-bezogene Header, sodass domänenübergreifende JavaScript-/Webview-Clients Fehlerantworten erfolgreich lesen können.

* Es wurde ein Problem mit X-Forwarded-For-Headern behoben, bei dem IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Anzeigen-Server weitergeleitet wurden.

* Es wurde ein Problem mit CMAF/demuxed Audio-Streams behoben, bei dem EXT-X-MEDIA-SEQUENCE-Nummern in bestimmten Szenarien falsch inkrementiert wurden.

### Version 20.1.3

**Wenn:** Dienstag, 28. Januar 2020 von 2:00 Uhr bis 03:00 Uhr OSTSEE

* **VMAP mit FER-Unterstützung für nbc CueFormat**

   Konvertieren Sie Hinweise vom FER-Stream in die FW-Zeitleiste, um Parameter zu überschreiben, wenn der Stream verwendet `ptcueformat=nbc` wird und ein VOD-Stream mit In-Manifest-Hinweisen und Backed-In-Anzeigen ist.

* Bereinigen Sie das Feld &quot;user-agent&quot;im HTTP-Header, bevor Sie es an Drittanbieter/CDN weiterleiten.

* Filtern Sie vor dem Senden an Auditude und andere Anzeigenanbieter (CDNs) die Steuerungs-/Nicht-Druckzeichen (ASCII-Code &lt; 32) aus HTTP-Headern des Benutzeragents heraus. Auditude Ad-Call hat bei solchen ungültigen Headern früher nicht funktioniert.

* Entfernen Sie alte V1-Objekte aus NetStorage-Gruppen, um die Objektanzahl innerhalb sicherer Grenzen von Akamai zu halten.

## Behobene Probleme

Wenn die Lösung mit einem gemeldeten Problem verbunden ist, wird ein Zendesk-Verweis angezeigt. Beispiel: ZD#xxxxx.

**PTAI 20.3.3**

* Problem mit X-Forwarded-For-Headern, bei denen IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Anzeigen-Server weitergeleitet wurden.

* Problem mit CMAF/demuxed Audio-Streams, bei denen in bestimmten Szenarien EXT-X-MEDIA-SEQUENCE-Zahlen in bestimmten Szenarien falsch inkrementiert werden

## Bekannte Probleme und Einschränkungen

**PTAI 20.3.3**

Keine neue Einschränkung hinzugefügt.
