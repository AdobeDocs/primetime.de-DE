---
title: Primetime Offline Packager 2.x-Versionen
seo-title: Primetime Offline Packager 2.x-Versionen
description: Neue Funktionen in Primetime Offline Packager 2.1 und 2.3.1
seo-description: Neue Funktionen in Primetime Offline Packager 2.1 und 2.3.1
uuid: 01926a10-890d-477d-b832-e22847d957e0
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 933a0711-846a-4bb7-bf51-b300822a93d4
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Primetime Offline Packager-Versionen {#primetime-offline-packager-x-releases}

Neue Funktionen in Primetime Offline Packager 2.1 und 2.3.1

## Neue Funktionen in Primetime Offline Packager 2.3.1 (Oktober 2016) {#what-s-new-in-primetime-offline-packager-oct}

Die Version aktiviert On-Demand-Profil für MPEG-DASH, unterstützt die Option `validate` für das PlaylistCreator-Tool und hat wenige wichtige Korrekturen für die unten aufgeführten Multi-DRM-Szenarien.

| **Ausgabenummer** | **Beschreibung** |
|---|---|
| PTPUB-985 | HLS AAXS und Sample-AES funktionieren nicht für vom Packager generierten Schlüssel |
| PTPUB-973 | Korrektur des Fehlers beim Verschlüsselungsalgorithmus für bestimmte Weitwinkelinhalte |
| PTPUB-964 | CENC-Verschlüsselung für bestimmte Medientypen auf bestimmten Playern - Android TVSDK. |
| PTPUB-954 | Die AES-Verschlüsselung umgeht AAXS DRM standardmäßig / Fehler, der bei aktiviertem Remote-Key-Versand ausgegeben wird. |
| PTPUB-951 | Offline Packager gibt keine Ausnahme aus, wenn key_file_path nicht mit Widevine angegeben wurde. Stattdessen wird NPE geworfen. |

Die aktuelle Dokumentation zu Primetime Packagers finden Sie unter [https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

### Bekanntes Problem in Version 2.3.1 {#known-issue-in-version}

Die folgenden Probleme treten in dieser Version auf.

| **Ausgabenummer** | **Beschreibung** |
|---|---|
| PTPUB-1005 | PlaylistCreator stellt nicht die richtige URL für die .pssh-Datei in der endgültigen .mpd-Datei auf Setebene bereit, die für das AAXS DRM generiert wurde. |
| PTPUB-1001 | PlaylistCreator sollte Fehler auslösen, wenn leerer Pfad über den Parameter in_path bereitgestellt wird |
| PTPUB-990 | Für DASH schreibt Offline Packager keinen Paketersteller, der IV auf Festplatte generiert hat, wenn die Parameter `log_vi` und `iv_out_path` angegeben wurden. |
| PTPUB-980 | Wenn die Konfigurationsdatei zum Verpacken verwendet wird, entfernt der Parameter `key_url` die Anführungszeichen nicht aus den bereitgestellten Eingaben. |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### Mindestsystemanforderungen {#minimum-system-requirements}

Unterstützte Betriebssysteme

* Linux CentOS 6.3 64 Bit

Hardwareanforderungen

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder schneller empfohlen)

* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)

* Festplatte

(Disk-SAS): Mindestens 10 GB mit 7,5 K RPM

(Disk-SSD): 400 MBps Lese-/Schreibgeschwindigkeit

(NAS): 1 GB dedizierter Link

Softwareanforderungen

* Oracle Java SE 1.8 oder höher

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Laden Sie die Java SE-Software von der [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) herunter und befolgen Sie die Installationsanweisungen.
1. Extrahieren Sie die Adobe Primetime Offline Packager 2.3.1-Archivdatei mit dem Namen `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` auf die Festplatte.

### Konfigurieren von Offline Packager 2.3.1 {#configuring-the-offline-packager}

Die Konfigurationsanweisungen sind im Handbuch Erste Schritte mit Primetime Offline Packager unter [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html) verfügbar

## Neue Funktionen in Primetime Offline Packager 2.1 (Juli 2015) {#what-s-new-in-primetime-offline-packager-july}

Unterstützung für PlayReady BuyDRM (für DASH). Weitere Informationen finden Sie in der Hilfe Dokumentation [hier ](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

Die folgenden Verbesserungen wurden auch am Offline-Packager vorgenommen.

PTPUB-780 Zusätzliche Unterstützung für EXT-X-BEGINN-Tag

## Neue Funktionen in Primetime Offline Packager 2.0 (Juni 2015) {#what-s-new-in-primetime-offline-packager-june}

Die DASH-Ausgabenunterstützung wurde entfernt. Weitere Informationen finden Sie in der Produktdokumentation [hier](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

Folgende Probleme wurden in dieser Version ebenfalls behoben.

* PTPUB-783 Offline Packager kann jetzt leere WebVTT-Dateien verarbeiten.
* PTPUB- 781 Artifacts in HLS geben in Chrome aus, wenn bestimmte transkodierte MP4-Assets mit Offline-Packager verpackt werden, um eine MBR-Ausgabe zu erzeugen.

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### Mindestsystemanforderungen {#minimum-system-requirements-1}

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder schneller empfohlen)

* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)

* 1-Gbit-Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)

* Festplatte

   * (Disk-SAS): Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD): 400 MBps Lese-/Schreibgeschwindigkeit
   * (NAS): 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java SE 1.8 oder höher

### Installieren von Offline Packager 2.1 {#installing-offline-packager}

1. Laden Sie die Java SE-Software von der [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) herunter und befolgen Sie die Installationsanweisungen.
1. Extrahieren Sie das `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip` auf Ihre Festplatte.

### Konfigurieren von Offline Packager 2.1 {#configuring-the-offline-packager-1}

Die Konfigurationsdetails finden Sie im Dokument Erste Schritte mit Primetime Offline Packager unter [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).