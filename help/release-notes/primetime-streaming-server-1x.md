---
title: Primetime Streaming Server-Versionen
seo-title: Primetime Streaming Server 1.x-Versionen
description: Neue Funktionen in den Versionen Primetime Streaming Server 1.3 und 1.4.
seo-description: Neue Funktionen in den Versionen Primetime Streaming Server 1.3 und 1.4.
uuid: be05db6b-713f-4406-940d-9f3a805f967b
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: baec714e-9d41-4e8b-b134-13a736885cbd
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1929'
ht-degree: 0%

---


# Primetime-Streaming-Server-Versionen {#primetime-streaming-server-x-releases}

Neue Funktionen in den Versionen Primetime Streaming Server 1.3 und 1.4.

## Neu in Primetime Streaming Server 1.4 (Dezember-Version) {#what-s-new-in-primetime-streaming-server-december-release}

**Offline Packager**

* Ausgabe-HLS-Streams enthalten jetzt ID3-Metadaten, die in MPEG-2 TS vorhanden sind
* HLS-Audio-Streams können nun über ein zugewiesenes statisches Bild verfügen
* Unterstützung für die Bereitstellung von IV als Benutzereingabe für HLS AES-Verschlüsselung Workflows
* Unterstützung der Ausgabe von IV in eine Datei, wenn IV vom Offline-Packager generiert wird
* Playlist Creator unterstützt jetzt das Verknüpfen von mehrsprachigen Audiogruppen und mehrsprachigen WebVTT-Untertitelgruppen mit Medienströmen

**Herkunft Server**

* HLS AES-Verschlüsselung ist für Live- und VOD-Workflows verfügbar. Primetime Herkunft kann Just in Time HLS AES Verschlüsselung auf eingehende HLS-Streams oder MP4-Dateien anwenden.
* Es kann auch eine JIT HLS AES-Verschlüsselung anwenden, wenn es zum Konvertieren eingehender HDS-Streams in HLS-Streams verwendet wird.
* Primetime-Herkunft unterstützt jetzt SWF-Listen für PHLS-Streams. Früher wurde es nur für PHDS-Streams unterstützt

**Primetime Live Packager**

* Unterstützung zum Generieren von HLS AES-128-Streams für Eingabe-RTMP- und MPEG-2-TS-Streams

Die Zertifikate PHDS/PHLS wurden aktualisiert. Das neue Ablaufdatum für dasselbe Datum ist der 10.1.2016.

### **Fehlerbehebungen in Version 1.4** {#bug-fixes-included-in-release}

* PTPUB-282- Das von OfflinePackager 1.3.1 erstellte HLS-Manifest verfügt nicht über Codec- und Auflösungsinformationen.
* PTPUB-353 - PlayListCreator unterstützt nicht das Hinzufügen von WebVTT-Informationen zum Manifest auf der festgelegten Ebene
* PTPUB-583 - PlaylistCreator-Tool stellt unerwartet Gruppen-URIs vor.
* PTPUB-605 Playlist Creator listet nicht die SUBTITLE-Gruppe in jedem Variantenstream auf
* PTPUB-634 -Offline Packager fügt SpliceInsert zu manifest hinzu.
* PTPUB-635- Mehrere SpliceOut-Tags, die für ein einzelnes Anzeigen-Cue eingefügt wurden.

### Bekanntes Problem in Version 1.4 {#known-issue-in-release}

* PTPUB-645 DPISimple-Modus wird erzwungen, auch wenn der DPIScte35-Modus angegeben wird, wenn sowohl Befehlszeilenbefehle als auch In-Stream-Hinweise in der Offline-Paketkonfiguration bereitgestellt werden

## Neue Funktionen in Primetime Streaming Server 1.3.1 (MAY Release) {#what-s-new-in-primetime-streaming-server-may-release}

Version 1.3.1 bezieht sich auf den Hotfix. Die folgenden Verbesserungen machen es zu einem empfohlenen Upgrade für Kunden, da es aus wichtigen Leistungsverbesserungen für JIT MP4-Anwendungsfälle besteht:

1. Leistungskorrektur der MP4 JIT m3u8-Generation auf Herkunft mit DRM einschließlich Schlüsseldrehung
1. Die Konfiguration &quot;CopyQueryParamToJITFragmentURIs&quot;wurde hinzugefügt, um Abfragen-Parameter aus der JIT-Manifestanforderung in generierte Fragment-URIs für die MP4-JIT-Konvertierung zu kopieren. Beispiele zur Verwendung finden Sie in der Dokumentation zu HTTP Herkunft Server
1. Zulassen von MP4-Dateien ohne Erweiterung für die JIT-Konvertierung über die zu vod.xml hinzugefügte Konfiguration &quot;Config/MP4Only&quot;

### Fehlerbehebungen in Version 1.3.1 {#bug-fixes-included-in-release-1}

* 3759167 - Nicht alle SCTE35-Hinweise führen aufgrund einer Zeitstempelanomalie beim Verpacken zum Ausgabemmanifest. Wenden Sie im TimeSignal von SpliceInfoSection in der SCTE35-Meldung pts_Adjustment an.

### Bekannte Probleme in Version 1.3.1 {#known-issues-in-release}

* 3717039 - Wenn der Packager so konfiguriert ist, dass DPI-Sätze im einfachen Modus erzeugt werden, sollte er wirklich nach bestimmten Signaltypen suchen, z. B. Spleice-Einfüge oder Platzierungsmöglichkeiten, und nur diese in einfache Modus-Hinweise konvertieren. Sie sollte andere Signaltypen wie Programm-Beginn, Netzwerk-Beginn usw. ignorieren.

* 3718598 - Wenn Herkunft Server für die Bereitstellung geschützter Inhalte mit aktiviertem HSM-Zugriff konfiguriert ist, führt der Backend-LunaSA-Client eine häufige Kommunikation mit dem HSM-Modul durch

## Neue Funktionen in Primetime Streaming Server 1.3 (APRIL-Version) {#what-s-new-in-primetime-streaming-server-april-release}

Primetime 1.3 bietet verschiedene neue Funktionen rund um Streaming-Inhalte, bessere Benutzerfreundlichkeit und Sicherheit.

**Primetime Streaming Server als einheitliche Form von Live Packager und Herkunft Server**

Primetime Live Packager und Primetime-Herkünfte werden zusammengeführt, um als eine Komponente zu funktionieren. Diese Komponente kann als Packager oder als Herkunft verwendet werden oder die kombinierten Funktionen zum Verpacken und Hosten eines Live-Streams verwenden.

Dadurch erhalten diese Server eine einheitliche Dateischnittstelle, sodass sie auf einem einzigen Computer problemlos ausgeführt werden können. Es bietet weiterhin die Flexibilität, als separater Packager oder als separate Herkunft konfiguriert zu werden.

**Beta MPEG- DASH-Unterstützung**

Primetime Streaming Server unterstützt MPEG-DASH-Verpackungen für Live- und VOD-Workflows. Die Live Packager-Komponente konvertiert die infizierten RTMP- oder MPEG-2-TS-Streams in das DASH-Format. Die Herkunft akzeptiert einen DASH-Stream.

Bei VOD-Workflows konvertiert die Offline Packager-Komponente MP4- und TS-Elemente in das MPEG-DASH-ISOBFF-Format.

**Live-zu-VOD-Konvertierung**

Eine neue Komponente Recording Server ist jetzt verfügbar, die die Erfassung eines Live-Streams und die Archivierung für die VOD-Wiedergabe unterstützt. Es unterstützt die Erstellung von Full-Ereignis-Wiederholungen sowie Clips/Highlights für einen Teil des Ereignisses. Es kann so konfiguriert werden, dass nur Audio-Streams aufgezeichnet werden, Anzeigen entfernt oder in Live-Inhalten aufgenommen werden. Recording Server funktioniert sowohl mit Primetime Streaming Server als auch mit Herkünfte von Drittanbietern.

**RTMP-zu-HLS-Konvertierung in Primetime Live Packager**

Die Primetime Live Packager-Komponente unterstützt die Erstellung von HLS-Streams aus RTMP-Streams. Außerdem können Primetime DRM und Protected Streaming zu den Ausgabe-HLS-Streams hinzugefügt werden.

**Authentifizierung für eingehende RTMP-Streams an Primetime Live Packager**

Eine usermgmt.jar-Datei wird jetzt mit Primetime Live Packager ausgeliefert, um den Zugriff mit vertrauenswürdigen Anmeldeinformationen zu konfigurieren, wenn ein RTMP-Stream an Primetime Live Packager gesendet wird

Jetzt können die Kodierer so konfiguriert werden, dass sie beim Senden von Streams an Live Packager einen Benutzernamen/ein Passwort verwenden.

**PlaylistCreator-Tool zum Erstellen von Manifesten auf oberster Ebene für HDS und HLS**

Mit dem Primetime Offline Packager ist jetzt ein Dienstprogramm PlaylistCreator.jar verfügbar, mit dem Sie mühelos Manifestdateien der obersten Ebene für HDS- und HLS-Assets erstellen können.

**Zusätzliche Sicherheitsfunktion zum Einbauen eines Hardware-Sicherheitsmoduls**

Primetime Offline Packager unterstützt jetzt den Zugriff auf das Packager-Berechtigungszertifikat und allgemeine Schlüssel über ein Hardware-Sicherheitsmodul.

Ein Hardware-Sicherheitsmodul bietet zusätzlichen Schutz für diese vertraulichen Elemente.

**Verbesserte Leistung für VOD-Verpackungen**

Mehrere Leistungsverbesserungen wurden integriert, um die Verpackungszeit für Mezzanine-Assets im Primetime Offline Packager zu verbessern

**Verbesserte Leistung für JIT MP4-Packaging**

In die JIT-Verpackungsfunktionen von Primetime Herkunft wurden mehrere Leistungsverbesserungen integriert, um Benutzeranforderungen für eine große Bibliothek von VOD-Assets zu bearbeiten.

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### Mindestsystemanforderungen {#minimum-system-requirements}

**Netzanforderungen**

* Das Netzwerk sollte Multicast-fähig sein, um den MPEG-TS-Stream von einem Encoder an Live Packager zu senden. Live Packager akzeptiert auch einen RTMP-Stream von einem Encoder, für den kein Multicast-Netzwerk erforderlich ist.

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder schneller empfohlen)
* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)
* 1-Gbit-Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)
* Datenträger:

   * (Disk-SAS): Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD) : 400 MBps Lesen/Schreiben
   * (NAS): 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java JRE 1.7 (Empfehlung: Sun/Oracle Hotspot JVM). Das JDK ist für den Zugriff von JConsole auf die JMX-APIs erforderlich.

### Primetime Streaming Server {#install-and-configure-primetime-streaming-server} installieren und konfigurieren

**Installieren des Streaming-Servers**

1. Laden Sie die Java SE- und JDK-Software von der [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) herunter und befolgen Sie die Installationsanweisungen.
2. Extrahieren Sie die Archivdatei Adobe Primetime-Streaming Server 1.4, `Primetime- StreamingServer-1-4-0-b206-12042014.zip` auf Ihre Festplatte.

**Beginn des Primetime-Streaming-Servers**

Führen Sie zum Beginn des Streaming-Servers den folgenden Befehl über die Befehlszeile im Stammordner des Streaming-Servers aus:\
`$./pss_start.sh`

**Primetime Streaming Server als Live Packager oder HTTP Herkunft Server konfigurieren**

Um den Streaming Server als Live Packager oder Herkunft Server zu konfigurieren, aktualisieren Sie die Konfigurationsdatei &quot;pss.xml&quot;im Ordner &quot;conf&quot;im Stammordner des Streaming-Servers:

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**Primetime-Streaming-Server beenden**

Um den Streaming Server zu beenden, führen Sie den folgenden Befehl im Stammordner des Streaming-Servers aus:\
`$./pss_stop.sh`

**Primetime Streaming Server neu starten**

Um den Streaming-Server neu zu starten, beenden Sie den Streaming-Server und starten Sie den Beginn.

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Primetime Streaming Server deinstallieren**

Um den Streaming-Server zu deinstallieren, beenden Sie den Streaming-Server und entfernen Sie den Ordner &quot;pss&quot;des Streaming-Servers im Ordner &quot;Primetime&quot;

## Arbeiten mit Live Packager und Herkunft Server 1.4 {#working-with-live-packager-and-origin-server}

Dieser Abschnitt gilt, wenn Primetime Streaming Server nicht verwendet wird und stattdessen Primetime Live Packager UND/ODER Primetime Herkunft Server bereitgestellt wird.

### Mindestsystemanforderungen {#minimum-system-requirements-1}

**Netzanforderungen**

* Das Netzwerk sollte Multicast-fähig sein, um den MPEG-TS-Stream von einem Encoder an Live Packager zu senden. Live Packager akzeptiert auch einen RTMP-Stream von einem Encoder, für den kein Multicast-Netzwerk erforderlich ist.

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder schneller empfohlen)
* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)
* 1-Gbit-Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)
* Datenträger:

   * (Disk-SAS): Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD) : 400 MBps Lesen/Schreiben
   * (NAS): 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java JRE 1.7 (Empfehlung: Sun/Oracle Hotspot JVM). Das JDK ist für den Zugriff von JConsole auf die JMX-APIs erforderlich.

Die oben genannten Mindestsystemanforderungen gelten für Herkunft Server und Live Packager.

### Installieren und Konfigurieren von Live Packager {#install-and-configure-the-live-packager}

**Installieren von Live Packager**

1. Laden Sie die Java SE- und JDK-Software von der [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) herunter und befolgen Sie die Installationsanweisungen.
1. Extrahieren Sie die Archivdatei Adobe Primetime - Live Packager 1.4 `Primetime-LivePackager-1-4-0-b206-12042014.zip` auf Ihre Festplatte.

**Installieren des HTTP-Herkunft-Servers**

1. Laden Sie die Java JRE- und JDK-Software von der [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) herunter und befolgen Sie die Installationsanweisungen.
1. Extrahieren Sie die Archivdatei Adobe Primetime - HTTP Herkunft Server 1.4, `Primetime-HttpOrigin-1-4-0-b206-12042014.zip` auf Ihre Festplatte.

**Um Live** PackagerAuf den Beginn des Packager Beginn, führen Sie den folgenden Befehl aus dem Stammordner des Packager aus:\
`$packager_start.sh`

**So Beginn der HTTP-Herkunft**

Führen Sie zum Beginn des HTTP-Herkunft-Servers den folgenden Befehl über die Befehlszeile im Stammordner des Herkunft-Servers aus:\
`$./origin_start.sh`

**Live Packager beenden**

Um den Packager zu beenden, führen Sie den folgenden Befehl aus dem Stammordner des Packager aus:\
`$packager_stop.sh`

**HTTP-Herkunft-Server beenden**

Um den HTTP-Herkunft-Server zu beenden, führen Sie den folgenden Befehl im Stammordner des Herkunft-Servers aus:\
`$./origin_stop.sh`

**Starten Sie Live Packager neu**

Um den Packager neu zu starten, beenden Sie den Packager und führen Sie einen Beginn durch.

**Hinweis**: Wenn der Packager Beginn, versucht er, die Bootstrap-Informationen aus der Fragment-Zielgruppe im temporären Ordner zu initialisieren. Wenn die Bootstrap-Informationen in der Fragment-Zielgruppe gefunden werden, bedeutet dies, dass der Packager neu gestartet wurde. Bei einem Neustart wartet der Packager bis zum nächsten Fragmentrand und packt dann Beginn. Der Packager fügt einen Lückeneintrag in den Bootstrap ein, um anzuzeigen, dass fehlende Fragmente vorhanden sind.

**Starten Sie den HTTP-Herkunft-Server neu**

Um den HTTP-Herkunft-Server neu zu starten, beenden Sie den HTTP-Herkunft-Server und führen Sie ihn aus.

**Live Packager konfigurieren**

Die Distributionsdatei enthält eine Beispielkonfiguration, die zum Testen des Pakets verwendet werden kann.

Nachdem Sie das Archiv Adobe Primetime - Live Packager 1.4 extrahiert haben, ändern Sie die Ordner in den Ordner &quot;packager&quot;und führen Sie das Skript &quot;packager_Beginn.sh&quot;aus. Die Beispielkonfiguration überwacht die Multicast-Adresse 239.235.0.3:14000 und führt den lokalen Herkunft-Server an Port 8080 aus. Die Ausgabe ist so konfiguriert, dass sie in `packager/webroot/_default_/_default_/ directory` geschrieben wird.

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**HTTP-Herkunft-Server konfigurieren**

Die hier verfügbaren Konfigurationsdetails finden Sie im Dokument Erste Schritte mit Primetime HTTP Herkunft Server.

**Live Packager deinstallieren**

Um den Packager zu deinstallieren, beenden Sie den Packager und entfernen Sie den Ordner &quot;packager&quot;aus dem Ordner &quot;Primetime&quot;.

**Deinstallieren des HTTP-Herkunft-Servers**

Um den HTTP-Herkunft-Server zu deinstallieren, beenden Sie den HTTP-Herkunft-Server und entfernen Sie den HTTPS-Herkunft-Server-Ordner im Primetime-Ordner.

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### Mindestsystemanforderungen {#minimum-system-requirements-2}

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder schneller empfohlen)
* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)
* 1-Gbit-Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)
* Datenträger:

   * (Disk-SAS): Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD) : 400 MBps Lesen/Schreiben
   * (NAS): 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java JRE 1.7 oder höher.

### Installieren und Konfigurieren von Offline Packager {#install-and-configure-offline-packager}

Gehen Sie wie folgt vor, um Offline Packager zu installieren:

1. Laden Sie die Java SE-Software von der [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) herunter und befolgen Sie die Installationsanweisungen.
1. Extrahieren Sie die Archivdatei Adobe Primetime - Offline Packager 1.4, `Primetime- OfflinePackager-1-4-0-b206-12042014.zip` auf Ihre Festplatte.

Im Dokument Erste Schritte mit Primetime Offline Packager finden Sie die Konfigurationsdetails [hier](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).