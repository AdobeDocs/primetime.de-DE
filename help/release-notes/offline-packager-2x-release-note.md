---
title: Primetime Offline Packager 2.x-Versionen
description: Neue Funktionen in den Versionen Primetime Offline Packager 2.1 und 2.3.1
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Primetime Offline Packager-Versionen {#primetime-offline-packager-x-releases}

Neue Funktionen in den Versionen Primetime Offline Packager 2.1 und 2.3.1

## Neue Funktionen in Primetime Offline Packager 2.3.1 (Oktober 2016)  {#what-s-new-in-primetime-offline-packager-oct}

Die Version aktiviert On-Demand-Profil für MPEG-DASH, fügt Unterstützung für die `validate` -Option für das PlaylistCreator-Tool verwendet und es gibt unten einige wichtige Fehlerbehebungen für Multi-DRM-Szenarien.

| **Nummer des Problems** | **Beschreibung** |
|---|---|
| PTPUB-985 | HLS AAXS und Sample-AES funktionieren nicht für vom Packager generierten Schlüssel |
| PTPUB-973 | Fehlerkorrektur - Verschlüsselungsalgorithmus für einen bestimmten umfangreichen Inhalt |
| PTPUB-964 | CENC-Verschlüsselung für bestimmte Medientypen auf bestimmten Playern unterbrochen - Android TVSDK. |
| PTPUB-954 | Die Sample-AES-Verschlüsselung umgeht standardmäßig AAXS DRM / Fehler bei aktivierter Remote-Schlüsselbereitstellung. |
| PTPUB-951 | Der Offline-Packager löst keine Ausnahme aus, wenn key_file_path nicht mit Widevine angegeben ist. Stattdessen wird NPE ausgegeben. |

Die aktuelle Dokumentation zu Primetime Packagern finden Sie unter [https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

### Bekanntes Problem in Version 2.3.1 {#known-issue-in-version}

Die folgenden Probleme treten in dieser Version auf.

| **Nummer des Problems** | **Beschreibung** |
|---|---|
| PTPUB-1005 | PlaylistCreator stellt nicht die richtige URL für die .pssh-Datei in der endgültigen .mpd-Datei auf Setebene bereit, die für das AAXS DRM generiert wurde. |
| PTPUB-1001 | PlaylistCreator sollte einen Fehler ausgeben, wenn ein leerer Pfad über den Parameter in_path bereitgestellt wird |
| PTPUB-990 | Für DASH schreibt Offline Packager den IV generierten Packager nicht auf die Festplatte, wenn die Parameter `log_vi` &amp; `iv_out_path` angegeben werden. |
| PTPUB-980 | Wenn die Konfigurationsdatei für die Verpackung verwendet wird, wird der Parameter verwendet `key_url` entfernt die Anführungszeichen nicht aus den bereitgestellten Eingaben. |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### Mindestsystemanforderungen {#minimum-system-requirements}

Unterstützte Betriebssysteme

* Linux CentOS 6.3 64 Bit

Hardwareanforderungen

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder höher empfohlen)

* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)

* Festplatte

(Disk-SAS): Mindestens 10 GB mit 7,5 K RPM

(Disk-SSD): Lese-/Schreibgeschwindigkeit 400 MBit/s

(NAS): 1 GB dedizierter Link

Softwareanforderungen

* Oracle Java SE 1.8 oder höher

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Laden Sie die Java SE-Software aus dem [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) und befolgen Sie die Installationsanweisungen.
1. Extrahieren Sie die Adobe Primetime Offline Packager 2.3.1-Archivdatei mit dem Namen `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` auf den Datenträger.

### Konfigurieren von Offline Packager 2.3.1 {#configuring-the-offline-packager}

Die Konfigurationsanweisungen finden Sie im Erste-Schritte-Handbuch zu Primetime Offline Packager unter [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Neue Funktionen in Primetime Offline Packager 2.1 (Juli 2015) {#what-s-new-in-primetime-offline-packager-july}

Unterstützung für PlayReady BuyDRM (für DASH). Weitere Informationen finden Sie in der Hilfedokumentation [hier verfügbar](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

Die folgenden Verbesserungen wurden auch am Offline-Packager vorgenommen.

PTPUB-780 Unterstützung für EXT-X-START-Tag hinzugefügt

## Neue Funktionen in Primetime Offline Packager 2.0 (Juni 2015) {#what-s-new-in-primetime-offline-packager-june}

Es wurde eine deutliche DASH-Ausgabeunterstützung hinzugefügt. Siehe Produktdokumentation . [here](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html) für Details.

Die folgenden Probleme wurden in dieser Version ebenfalls behoben.

* PTPUB-783 Offline Packager kann jetzt leere WebVTT-Dateien verarbeiten.
* PTPUB- 781 Artifacts in HLS-Ausgabe in Chrome, wenn bestimmte transkodierte MP4-Assets mit Offline-Packager gepackt werden, um eine MBR-Ausgabe zu generieren.

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### Mindestsystemanforderungen {#minimum-system-requirements-1}

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder höher empfohlen)

* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)

* 1 Gbit Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)

* Festplatte

   * (Disk-SAS): Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD): Lese-/Schreibgeschwindigkeit 400 MBit/s
   * (NAS): 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java SE 1.8 oder höher

### Installieren von Offline Packager 2.1 {#installing-offline-packager}

1. Laden Sie die Java SE-Software aus dem [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) und befolgen Sie die Installationsanweisungen.
1. Extrahieren Sie die `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`, auf Ihre Festplatte.

### Konfigurieren von Offline Packager 2.1 {#configuring-the-offline-packager-1}

Die hier verfügbaren Konfigurationsdetails finden Sie im Dokument Erste Schritte mit Primetime Offline Packager . [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
