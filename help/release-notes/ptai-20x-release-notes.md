---
title: Versionshinweise zu PTAI 20.12.1
description: Die PTAI-Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in Primetime Ad Insertion im Jahr 2020.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1081'
ht-degree: 0%

---

# Primetime Ad Insertion 20.12.1 - Versionshinweise

Die Primetime-Ad Insertion-Versionshinweise 20.12.1 beschreiben, was neu ist oder geändert wurde, Probleme gelöst wurden und bekannte Probleme in Primetime Ad Insertion im Jahr 2020.

## Neue Funktionen in PTAI 20.12.1

**Wenn:** Dienstag, 8. Dezember 2020 von 01:00 Uhr bis 04:00 Uhr Ostzeit

**Änderungen**

* Enthält Hotfix zur Behebung zeitweiliger Probleme bei der Client-Konnektivität (5xx) beim Primetime-Ad Insertion am 30. November 2020.

## Verbesserungen und Fehlerbehebungen in früheren Versionen

### Version 20.11.1

**Wenn:** Donnerstag, 5. November 2020 von 2:00 Uhr bis 05:00 Uhr Ostzeit

**Änderungen**

* Wartungs-Updates.

### Version 20.10.2

**Wenn:** Donnerstag, 29. Oktober 2020 von 12:01 Uhr bis 06:00 Uhr Ostzeit

**Änderungen**

* Wartungs-Updates.

### Version 20.10.1

**Wenn:** Dienstag, 13. Oktober 2020 von 03:00 Uhr bis 07:00 Uhr Ostzeit

**Änderungen**

* Wartungs-Updates.

### Version 20.9.3

**Wenn:** Mittwoch, 30. September 2020 um 3:30 Uhr bis 6:30 Uhr Ostzeit

**Änderungen**

* Bootstrap-API-Parameter hinzugefügt `ptparallelstream`. Dadurch können Kunden mit Playern, die parallel CMAF-demuxed Audio- oder Videostreams anfordern, sicherstellen, dass Anzeigen in Audio- und Videospuren konsistent sind. Setzen Sie den Parameterwert auf &quot;true&quot;, um diese Funktion zu aktivieren, oder lassen Sie die Deaktivierung weg.

### Version 20.9.2

**Wenn:** Dienstag, 15. September 2020 von 3:30 Uhr bis 6:30 Uhr Ostzeit

**Verbesserungen**

* Unterstützung für die Einbeziehung nicht-linearer Anzeigentypen mithilfe von `EXT-X-MARKER` Tags.
Weitere Informationen oder die Aktivierung dieser Funktion erhalten Sie von Ihrem Support-Mitarbeiter.

* Unterstützung für die Beschränkung der gesamten Anzeigenauflösungszeit, wenn die Reaktion der Anbieter zu lange dauert. Um die Begrenzung zu aktivieren, legen Sie den Bootstrap-API-Parameter fest `ptadtimeout` auf einen Wert in Millisekunden.

  >[!NOTE]
  >
  >Diese Zeitüberschreitung gilt nur für Anzeigenanfragen, nicht für Anzeigenanfragen.

### Version 20.9.1

**Wenn:** Dienstag, 1. September 2020 von 3:30 Uhr bis 7:30 Uhr Ostzeit

**Änderungen**

* Es wurde ein Problem für Kunden behoben, die HLS/CMAF verwenden und bei denen EXT-X-MAP manchmal CDN-Token oder EXT-X-MAP-Tags fehlten, die manchmal fälschlicherweise aus dem DVR-Fenster ausgerollt wurden.

### Version 20.8.4

**Wenn:** Mittwoch, 19. August 2020 von 03:30 Uhr bis 07:30 Uhr Ostzeit

**Verbesserungen und Fehlerbehebungen**

Wartungs-Updates.

### Version 20.8.1

**Wenn:** Dienstag, 4. August 2020 von 3:00 Uhr bis 6:00 Uhr Ostzeit

**Verbesserungen und Fehlerbehebungen**

Wartungs-Updates.

### Version 20.7.1

**Wenn:** Donnerstag, 9. Juli 2020 von 03:00 Uhr bis 05:00 Uhr Ostzeit

**Neue Funktionen und Verbesserungen**

* SCTE35-Verbesserung zur Verwendung von Start-/Endmeldungen von Provider-Anzeigen oder Break Start-/End-Meldungen, um den Cue-Point zu identifizieren.

* Der Header X-ADBE-AI-X1 wurde um zusätzliche Informationen zur Fehlerbehebung erweitert.

* Erweiterte Aggregation von Metriken.

* Verbessertes SSAI-Konsolen-Dashboard für den Bereich Sitzungsstatistik

### Version 20.6.2

**Wenn:** Donnerstag, 18. Juni 2020 von 03:00 Uhr bis 04:00 Uhr Ostzeit

**Verbesserungen**

Verbesserte Stream-Synchronisation für Video-Clients, die eine Genauigkeit von Millisekunden erfordern. Adobe-Support kontaktieren, um Millisekunde-Genauigkeit für `#EXT-X-PROGRAM-DATE-TIME tags`.

### Version 20.6.1

**Wenn:** Dienstag, 2. Juni 2020 von 03:00 Uhr bis 05:00 Uhr Ostzeit

**Neue Funktionen**

Wenden Sie sich an den Adobe-Support , um die folgenden neuen Funktionen über die serverseitige Konfiguration zu aktivieren:

* Manifestverwaltung: HLS-Segment- und Ressourcen-URLs können jetzt zwischen HTTP und HTTPS transformiert werden, um die Leistung zu steigern, indem TLS-Handshakes bei Back-End-Anforderungen reduziert werden. Sie kann auch verwendet werden, um Anzeigen-/Inhaltsfragmente auf denselben CDNs zu vereinheitlichen.

* Long Form VOD: Verbesserte APIs zur Beibehaltung der Sitzungsdauer mit langen VOD-Assets.

**Fehlerbehebungen**

* Es wurde ein Problem behoben, bei dem WebVTT-Fragmente unabhängig vom angeforderten Originalprotokoll immer unter dem HTTP-Protokoll angefordert wurden.

* Es wurde ein Problem behoben, bei dem EXT-X-DISCONTINUITY -Tags vom Anfang der Wiedergabeliste entfernt wurden, wenn von Anzeigen zurück zu Inhalten gewechselt wurde. Wenden Sie sich an den Adobe-Support , um diese Fehlerbehebung zu aktivieren.

### Version 20.5.1

**Wenn:** Dienstag, 5. Mai 2020 von 04:00 Uhr bis 05:00 Uhr Ostzeit

* Es wurde ein Fehler behoben, der sicherstellte, dass beim Senden von If-Modified-Since -Headern korrekte CORS-Header bereitgestellt werden.

* Fehlerbehebungen im CRS-Dashboard.

* Wartungs-Updates.

### Version 20.3.4

**Wenn:** Mittwoch, 1. April 2020 von 03:00 Uhr bis 04:00 Uhr Ostzeit

* Es wurde ein Fehler behoben, der dazu führte, dass Untertitel nach dem Einfügen einer Anzeige in VOD/WebVTT nicht mehr synchronisiert wurden.

* Sicherheitsupdates.

### Version 20.3.3

**Wenn:** Donnerstag, 26. März 2020 von 03:00 Uhr bis 04:00 Uhr Ostzeit

* SSAI 4XX- und 5XX-Antworten liefern nun ordnungsgemäß CORS-bezogene Kopfzeilen, sodass domänenübergreifende JavaScript-Webansichtsclients Fehlerantworten erfolgreich lesen können.

* Es wurde ein Problem mit Headern vom Typ X-Forwarded-For behoben, bei denen IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Anzeigen-Server übergeben wurden.

* Es wurde ein Problem mit CMAF/demuxed Audio-Streams behoben, bei dem die Anzahl der EXT-X-MEDIA-SEQUENCE-Zahlen in bestimmten Szenarien falsch erhöht wurde.

### Version 20.3.2

**Wenn:** Mittwoch, 11. März 2020 von 05:30 Uhr bis 07:00 Uhr Ostzeit

* Verbesserungen bei der Signalverarbeitung SCTE35.

* Wartungs-Updates.

### Version 20.3.1

**Wenn:** Donnerstag, 5. März 2020 von 02:30 Uhr bis 04:30 Uhr Ostzeit

* Leistungsverbesserungen:

   * Die Cache-Unterstützung für Master-/Media-m3u8-Manifeste wurde hinzugefügt. Diese Manifeste reagieren jetzt auf Cache-Control: öffentliche und Max-Age-Header, die häufig die Videostartleistung verbessern können.

   * Unterstützung für das Erzwingen des Abrufs von HTTPS-kreativen Elementen über HTTP hinzugefügt, wodurch auch die Videostartleistung verbessert werden kann.

* Sicherheits- und Wartungskorrekturen.

### Version 20.2.1

**Wenn:** Donnerstag, 13. Februar 2020 von 04:30 Uhr bis 05:30 Uhr Ostzeit

* Unterstützung für das Stitching von Anzeigen-Assets hinzugefügt, die mehrere reine Audiostreams enthalten, die auf Sprache/Codec/Bitrate basieren.
* Geringfügige Leistungsverbesserungen und Wartungsupdates.

### Version 20.1.3

**Wenn:** Dienstag, 28. Januar 2020 von 2:00 Uhr bis 03:00 Uhr Ostzeit

* **VMAP mit FER-Unterstützung für nbc CueFormat**

  Konvertieren von Hinweisen aus FER-Stream in Parameter zur Überschreibung von FW-Zeitleisten `ptcueformat=nbc` wird verwendet und der Stream ist ein VOD-Stream mit In-Manifest-Hinweisen und Backed-in-Anzeigen.

* Bereinigen Sie das Feld &quot;user-agent&quot;im HTTP-Header, bevor Sie es an Drittanbieter von Anzeigen/CDN weiterleiten.

* Filtern Sie Kontroll-/Nicht-druckbare Zeichen (ASCII-Code &lt; 32) aus HTTP-Headern für Benutzeragenten, bevor Sie sie an Auditude und andere Anzeigenanbieter, CDNs, senden. Auditude Ad-Call, der für solche ungültigen Kopfzeilen verwendet wurde, schlägt fehl.

* Bereinigen Sie alte V1-Objekte von NetStorage-Gruppen, um die Objektanzahl innerhalb sicherer Grenzen von Akamai zu halten.

### Version 20.1.2 (Hotfix)

**Wenn:** Montag, 20. Januar 2020 von 02:00 Uhr bis 03:00 Uhr Ostzeit

* Wartungs-Updates.

### Version 20.1.1

**Wenn:** Mittwoch, 15. Januar 2020 von 04:00 Uhr bis 05:00 Uhr Ostzeit

* Der Creative Repackaging-Dienst ermöglicht jetzt ein schnelleres Einfügen von Anzeigen durch die automatische Blockierung von falsch formatierten Kreativen.

* Unterstützung für Phase 1 für das neue Cue-Format SCTE 35 beim serverseitigen Anzeigen-Einfügen hinzugefügt.

* Wartungsaktualisierungen.

## Gelöste Probleme {#Resolved-issues}

Wenn die Lösung mit einem gemeldeten Problem verknüpft ist, wird eine Zendesk-Referenz angezeigt. Beispiel: `ZD#xxxxx`.

**PTAI 20.9.1**

* Es wurde ein Problem für Kunden behoben, die HLS/CMAF verwenden und bei denen EXT-X-MAP manchmal CDN-Token oder EXT-X-MAP-Tags fehlten, die manchmal fälschlicherweise aus dem DVR-Fenster ausgerollt wurden.

**PTAI 20.6.1**

* `WebVTT` Fragmente wurden unabhängig vom angeforderten Originalprotokoll immer unter dem HTTP-Protokoll angefordert.

* `EXT-X-DISCONTINUITY` -Tags werden vom Anfang der Wiedergabeliste entfernt, wenn von Anzeigen zurück zu Inhalten gewechselt wird. Wenden Sie sich an den Adobe-Support , um diese Fehlerbehebung zu aktivieren.

**PTAI 20.5.1**

* Probleme mit CORS-Headern beim Senden von If-Modified-Since-Headern.

* Probleme im CRS-Dashboard.

**PTAI 20.3.4**

* Problem, das dazu führte, dass Untertitel nach dem Einfügen einer Anzeige in VOD/WebVTT nicht mehr synchronisiert wurden.

**PTAI 20.3.3**

* Problem mit X-Forwarded-For-Headern, bei denen IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Adserver übergeben wurden.

* Problem mit CMAF/demuxed Audio-Streams, bei denen in bestimmten Szenarien die EXT-X-MEDIA-SEQUENCE-Zahlen in bestimmten Szenarien falsch inkrementiert werden

## Bekannte Probleme und Einschränkungen

**PTAI 20.10.1**

Keine neue Einschränkung hinzugefügt.
