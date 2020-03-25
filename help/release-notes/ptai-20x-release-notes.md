---
title: PTAI 20.3.3 - Versionshinweise
description: Die Versionshinweise zu PTAI 20.3.3 beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in Primetime Dynamic Ad Insertion im Jahr 2020.
translation-type: tm+mt
source-git-commit: ededb36a0b460fff4644a3716b36971ff9454c37

---


# Primetime Dynamic Ad Insertion 20.3.3 - Versionshinweise

Versionshinweise zur dynamischen Anzeigeneinfügung 20.3.3 beschreiben, was neu oder geändert ist, gelöste Probleme und bekannte Probleme bei der Primetime-Einfügen dynamischer Anzeigen im Jahr 2020.

## Neue Funktionen in PTAI 20.3.3

**Wenn:** Donnerstag, 26. März 2020 von 03:00 Uhr bis 04:00 Uhr OST

* SSAI 4XX- und 5XX-Antworten liefern nun korrekt CORS-bezogene Header, sodass domänenübergreifende JavaScript-/Webview-Clients Fehlerantworten erfolgreich lesen können.

* Es wurde ein Problem mit X-Forwarded-For-Headern behoben, bei dem IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Anzeigen-Server weitergeleitet wurden.

* Es wurde ein Problem mit CMAF/demuxed Audio-Streams behoben, bei dem EXT-X-MEDIA-SEQUENCE-Nummern in bestimmten Szenarien falsch inkrementiert wurden

## Änderungen in früheren Versionen

### Version

**Wenn:**

### Version

**Wenn:**

## Behobene Probleme

Wenn die Lösung mit einem gemeldeten Problem verbunden ist, wird ein Zendesk-Verweis angezeigt. Beispiel: ZD#xxxxx.

**PTAI 20.3.3**

* Problem mit X-Forwarded-For-Headern, bei denen IPv6-Adressen nicht korrekt URL-kodiert wurden, wenn sie an die Anzeigen-Server weitergeleitet wurden.

* Problem mit CMAF/demuxed Audio-Streams, bei denen in bestimmten Szenarien EXT-X-MEDIA-SEQUENCE-Zahlen in bestimmten Szenarien falsch inkrementiert werden

## Bekannte Probleme und Einschränkungen

**PTAI 20.3.3**

Keine neue Einschränkung hinzugefügt.
