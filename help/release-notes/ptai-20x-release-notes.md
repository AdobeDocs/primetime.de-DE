---
title: PTAI 20.10.1 - Versionshinweise
description: Die Versionshinweise zu PTAI 20.10.1 beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in Primetime Ad Insertion im Jahr 2020.
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 0%

---


# Primetime Ad Insertion 20.10.1 - Versionshinweise

Die Versionshinweise Primetime Ad Insertion 20.10.1 beschreiben, was neu oder geändert ist, gelöste Probleme und bekannte Probleme in Primetime Ad Insertion im Jahr 2020.

## Neue Funktionen in PTAI 20.10.1

**Wenn:** Dienstag, 13. Oktober 2020 von 03:00 Uhr bis 07:00 Uhr östliche Zeit

**Änderungen**

* Aktualisierungen der Wartung.

### Verbesserungen und Fehlerbehebungen in früheren Versionen

#### Version 20.9.3

**Wenn:** Mittwoch, 30. September 2020 um 3:30 Uhr bis 6:30 Uhr östliche Zeit

**Änderungen**

* Der Bootstrap-API-Parameter wurde hinzugefügt `ptparallelstream`. Dadurch können Kunden mit Playern, die parallel CMAF-demuxed Audio- oder Videostreams anfordern, sicherstellen, dass Anzeigen in Audio- und Videospuren konsistent sind. Setzen Sie den Parameterwert auf true, um diese Funktion zu aktivieren oder zu deaktivieren.

#### Version 20.9.2

**Wenn:** Dienstag, 15. September 2020 von 3:30 Uhr bis 6:30 Uhr östliche Zeit

**Verbesserungen**

* Unterstützung für die Einbeziehung nicht-linearer Anzeigentypen mit `EXT-X-MARKER` -Tags.
Wenden Sie sich an Ihren Kundenbetreuer, um weitere Informationen zu erhalten oder diese Funktion zu aktivieren.

* Unterstützung für die Begrenzung der gesamten Anzeigenauflösungszeit, wenn die Reaktion der Anbieter zu lange dauert. Um die Begrenzung zu aktivieren, setzen Sie den bootstrap-API-Parameter `ptadtimeout` auf einen Wert in Millisekunden.

   >[!NOTE]
   >
   >Dieser Timeout gilt nur für Anzeigenanforderungen, nicht für Werbeanforderungen.

#### Version 20.9.1

**Wenn:** Dienstag, 1. September 2020 von 3:30 Uhr bis 7:30 Uhr östliche Zeit

**Änderungen**

* Korrektur des Fehlers bei Kunden, die HLS/CMAF verwenden, bei dem EXT-X-MAP manchmal CDN-Token oder EXT-X-MAP-Tags fehlten, die manchmal fälschlicherweise aus dem DVR-Fenster gerollt wurden.

#### Version 20.8.4

**Wenn:** Mittwoch, 19. August 2020 von 03:30 Uhr bis 07:30 Uhr östliche Zeit

**Verbesserungen und Fehlerbehebungen**

Aktualisierungen der Wartung.

#### Version 20.8.1

**Wenn:** Dienstag, 4. August 2020 von 3:00 Uhr bis 6:00 Uhr östliche Zeit

**Verbesserungen und Fehlerbehebungen**

Aktualisierungen der Wartung.

#### Version 20.7.1

**Wenn:** Donnerstag, 9. Juli 2020 von 03:00 Uhr bis 05:00 Uhr Eastern Time

**Neue Funktionen und Verbesserungen**

* SCTE35-Erweiterung, um entweder die Beginn-/Endmeldungen des Anbieters oder die Beginn-/Endmeldungen zu verwenden, um den Cue zu identifizieren.

* X-ADBE-AI-X1-Header mit zusätzlichen Informationen zur Fehlerbehebung aktualisiert.

* Erweiterte Metrikaggregation.

* Erweitertes SSAI-Konsolen-Dashboard für das Bedienfeld &quot;Sitzungsstatistik&quot;

#### Version 20.6.2

**Wenn:** Donnerstag, 18. Juni 2020 von 03:00 Uhr bis 04:00 Uhr Eastern Time

**Verbesserungen**

Verbesserte Stream-Synchronisierung für Video-Clients, die eine Genauigkeit von Millisekunden erfordern. Wenden Sie sich an die Support-Adobe, um die Millisekunden-Präzision für `#EXT-X-PROGRAM-DATE-TIME tags`.

#### Version 20.6.1

**Wenn:** Dienstag, 2. Juni 2020 von 03:00 Uhr bis 05:00 Uhr Eastern Time

**Neue Funktionen**

Wenden Sie sich an den Support für Adoben, um die folgenden neuen Funktionen über eine serverseitige Konfiguration zu aktivieren:

* Manifestverwaltung: HLS-Segment- und -Ressourcen-URLs können jetzt zwischen HTTP und HTTPS transformiert werden, um die Leistung zu erhöhen, indem TLS-Handshakes bei Back-End-Anforderungen reduziert werden. Sie kann auch verwendet werden, um Anzeigen-/Inhaltsfragmente auf denselben CDNs zu vereinheitlichen.

* VOD: Langform Verbesserte APIs, um die Sitzung mit langen VOD-Assets am Leben zu erhalten.

**Fehlerbehebungen**

* Es wurde ein Problem behoben, bei dem WebVTT-Fragmente unabhängig vom angeforderten Originalprotokoll immer unter dem HTTP-Protokoll angefordert wurden.

* Es wurde ein Problem behoben, bei dem EXT-X-DISCONTINUITY-Tags vom Anfang der Wiedergabeliste entfernt wurden, wenn von Anzeigen zu Inhalt zurückgekehrt wurde. Wenden Sie sich an den Support für Adoben, um diese Fehlerbehebung zu aktivieren.

#### Version 20.5.1

**Wenn:** Dienstag, 5. Mai 2020 von 04:00 Uhr bis 05:00 Uhr Eastern Time

* Es wurde ein Fehler behoben, der sicherstellte, dass beim Senden von if-Modified-Since-Headern korrekte CORS-Header bereitgestellt werden.

* Fehlerbehebungen am CRS-Dashboard.

* Aktualisierungen der Wartung.

#### Version 20.3.4

**Wenn:** Mittwoch, 1. April 2020 von 03:00 Uhr bis 04:00 Uhr Eastern Time

* Es wurde ein Fehler behoben, der dazu führte, dass Untertitel nach dem Einfügen der Anzeige in VOD/WebVTT nicht mehr synchronisiert wurden.

* Sicherheitsaktualisierungen.

#### Version 20.3.3

**Wenn:** Donnerstag, 26. März 2020 von 03:00 Uhr bis 04:00 Uhr Eastern Time

* SSAI 4XX- und 5XX-Antworten liefern jetzt korrekt CORS-bezogene Header, sodass domänenübergreifende JavaScript-Webview-Clients Fehlerantworten erfolgreich lesen können.

* Es wurde ein Problem mit X-Forwarded-For-Headern behoben, bei dem IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Anzeigen-Server weitergeleitet wurden.

* Es wurde ein Problem mit CMAF/demuxed Audio-Streams behoben, bei dem EXT-X-MEDIA-SEQUENCE-Nummern in bestimmten Szenarien falsch inkrementiert wurden.

#### Version 20.3.2

**Wenn:** Mittwoch, 11. März 2020 von 05:30 Uhr bis 07:00 Uhr östliche Zeit

* Verbesserte SCTE35-Signalverarbeitung.

* Aktualisierungen der Wartung.

#### Version 20.3.1

**Wenn:** Donnerstag, 05. März 2020 von 02:30 Uhr bis 04:30 Uhr Eastern Time

* Leistungsverbesserungen:

   * Cache-Unterstützung für Übergeordnet/media m3u8-Manifeste hinzugefügt. Diese Manifeste reagieren jetzt auf die Cachesteuerung: öffentliche und Max-Age-Kopfzeilen, die häufig die Leistung von Video-Beginn verbessern können.

   * Es wurde Unterstützung hinzugefügt, um zu erzwingen, dass HTTPS-kreative Elemente über HTTP abgerufen werden, was auch die Leistung von Video-Beginn verbessern kann.

* Sicherheits- und Wartungs-Fehlerbehebungen.

#### Version 20.2.1

**Wenn:** Donnerstag, 13. Februar 2020 von 04:30 Uhr bis 05:30 Uhr Ostzeit

* Unterstützung für das Zusammenfügen von Anzeigenelementen mit mehreren reinen Audiostreams, basierend auf Sprache/Codec/Bitrate.
* Geringfügige Leistungsverbesserungen und Wartungs-Updates.

#### Version 20.1.3

**Wenn:** Dienstag, 28. Januar 2020 von 2:00 Uhr bis 03:00 Uhr östliche Zeit

* **VMAP mit FER-Unterstützung für nbc CueFormat**

   Konvertieren Sie Hinweise vom FER-Stream in die FW-Zeitleiste, um Parameter zu überschreiben, wenn der Stream verwendet `ptcueformat=nbc` wird und ein VOD-Stream mit In-Manifest-Hinweisen und Backed-In-Anzeigen ist.

* Bereinigen Sie das Feld &quot;user-agent&quot;im HTTP-Header, bevor Sie es an Drittanbieter/CDN weiterleiten.

* Filtern Sie vor dem Senden an Auditude und andere Anzeigenanbieter (CDNs) die Steuerungs-/Nicht-Druckzeichen (ASCII-Code &lt; 32) aus HTTP-Headern des Benutzeragents heraus. Auditude Ad-Call hat bei solchen ungültigen Headern früher nicht funktioniert.

* Entfernen Sie alte V1-Objekte aus NetStorage-Gruppen, um die Objektanzahl innerhalb sicherer Grenzen von Akamai zu halten.

#### Version 20.1.2 (Hotfix)

**Wenn:** Montag, 20. Januar 2020 von 02:00 Uhr bis 03:00 Uhr Eastern Time

* Aktualisierungen der Wartung.

#### Version 20.1.1

**Wenn:** Mittwoch, 15. Januar 2020 von 04:00 Uhr bis 05:00 Uhr östliche Zeit

* Der Creative Repackage-Dienst ermöglicht jetzt eine schnellere Anzeigeneinfügung, indem er die Auflistung fehlerhafter kreativer Elemente automatisch sperrt.

* Unterstützung für Phase 1 für das neue Cue-Format SCTE 35 in serverseitiger Anzeigeneinfügung hinzugefügt.

* Wartungs-Upgrades.

## Behobene Probleme {#Resolved-issues}

Wenn die Lösung mit einem gemeldeten Problem verbunden ist, wird ein Zendesk-Verweis angezeigt. Beispiel, `ZD#xxxxx`.

**PTAI 20.9.1**

* Korrektur des Fehlers bei Kunden, die HLS/CMAF verwenden, bei dem EXT-X-MAP manchmal CDN-Token oder EXT-X-MAP-Tags fehlten, die manchmal fälschlicherweise aus dem DVR-Fenster gerollt wurden.

**PTAI 20.6.1**

* `WebVTT` Fragmente wurden immer unter dem HTTP-Protokoll angefordert, unabhängig vom ursprünglichen Protokoll angefordert.

* `EXT-X-DISCONTINUITY` -Tags werden von oben in der Wiedergabeliste entfernt, wenn von Anzeigen zurück zum Inhalt gewechselt wird. Wenden Sie sich an den Support für Adoben, um diese Fehlerbehebung zu aktivieren.

**PTAI 20.5.1**

* Probleme mit CORS-Headern beim Senden von if-Modified-Since-Headern.

* Probleme im CRS-Dashboard.

**PTAI 20.3.4**

* Problem, das dazu führte, dass Untertitel nach dem Einfügen der Anzeige in VOD/WebVTT nicht mehr synchronisiert wurden.

**PTAI 20.3.3**

* Problem mit X-Forwarded-For-Headern, bei denen IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Anzeigen-Server weitergeleitet wurden.

* Problem mit CMAF/demuxed Audio-Streams, bei denen in bestimmten Szenarien EXT-X-MEDIA-SEQUENCE-Zahlen in bestimmten Szenarien falsch inkrementiert werden

## Bekannte Probleme und Einschränkungen

**PTAI 20.10.1**

Keine neue Einschränkung hinzugefügt.
