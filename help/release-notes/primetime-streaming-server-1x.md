---
title: Primetime Streaming Server-Versionen
description: Neue Funktionen in den Versionen Primetime Streaming Server 1.3 und 1.4
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 0%

---

# Primetime Streaming Server-Versionen {#primetime-streaming-server-x-releases}

Neue Funktionen in den Versionen Primetime Streaming Server 1.3 und 1.4

## Neu in Primetime Streaming Server 1.4 (Dezember-Version) {#what-s-new-in-primetime-streaming-server-december-release}

**Offline Packager**

* Ausgabe-HLS-Streams enthalten jetzt in MPEG-2 TS vorhandene ID3-Metadaten
* Nur HLS-Audio-Streams können jetzt über zugehöriges statisches Bild verfügen
* Unterstützung für die Bereitstellung von IV als Benutzereingabe für HLS AES-Verschlüsselungs-Workflows
* Unterstützung der Ausgabe von IV in eine Datei, wenn IV vom Offline-Packager generiert wird
* Playlist Creator unterstützt jetzt die Zuordnung von mehrsprachigen Audio-Gruppen und mehrsprachigen WebVTT-Untertitelgruppen zu Medien-Streams

**Herkunftsserver**

* Die HLS AES-Verschlüsselung ist für Live- und VOD-Workflows verfügbar. Primetime Origin kann Just in Time HLS AES-Verschlüsselung auf eingehende HLS-Streams oder MP4-Dateien anwenden.
* Sie kann auch die JIT HLS AES-Verschlüsselung anwenden, wenn sie zum Konvertieren eingehender HDS-Streams in HLS-Streams verwendet wird.
* Primetime Origin unterstützt jetzt die SWF-Zulassungsauflistung für PHLS-Streams. Zuvor wurde dies nur für PHDS-Streams unterstützt

**Primetime Live Packager**

* Unterstützung zum Generieren von HLS AES-128-Streams für Eingabe-RTMP- und MPEG-2-TS-Streams

Die PHDS-/PHLS-Zertifikate wurden aktualisiert. Das neue Verfallsdatum für dasselbe wird am 10.1.2016 liegen.

### **Fehlerbehebungen in Version 1.4** {#bug-fixes-included-in-release}

* PTPUB-282 - Das von OfflinePackager 1.3.1 erstellte HLS-Set-Level-Manifest verfügt nicht über Codec- und Auflösungsinformationen.
* PTPUB-353 - PlayListCreator unterstützt nicht das Hinzufügen von WebVTT-Informationen zum Set Level Manifest
* PTPUB-583 - PlaylistCreator-Tool stellt unerwartet Gruppen-URIs vor.
* PTPUB-605 Playlist Creator listet die SUBTITLE-Gruppe nicht in den einzelnen Variantenstream auf
* PTPUB-634 -Offline Packager fügt SpliceInsert zu manifest hinzu.
* PTPUB-635 - Mehrere SpliceOut-Tags wurden für einen einzigen Anzeigen-Cue eingefügt.

### Bekanntes Problem in Version 1.4 {#known-issue-in-release}

* Der DPISimple-Modus PTPUB-645 wird auch dann erzwungen, wenn der DPIScte35-Modus angegeben ist, wenn sowohl Befehlszeilenbefehle als auch In-Stream-Hinweise in der Offline-Paketkonfiguration bereitgestellt werden.

## Neue Funktionen in Primetime Streaming Server 1.3.1 (Mai) {#what-s-new-in-primetime-streaming-server-may-release}

Version 1.3.1 bezieht sich auf den Hotfix. Die folgenden Verbesserungen machen es zu einem empfohlenen Upgrade für Kunden, da es aus wichtigen Leistungsverbesserungen für JIT MP4-Anwendungsfälle besteht:

1. Leistungskorrektur für MP4 JIT m3u8 Generation on Origin mit DRM einschließlich Schlüsselrotation
1. Die Konfiguration &quot;CopyQueryParamToJITFragmentURIs&quot;wurde hinzugefügt, um Abfrageparameter aus der JIT-Manifestanforderung in generierte Fragment-URIs für die MP4-JIT-Konvertierung zu kopieren. Beispielverwendung finden Sie in der Dokumentation zu HTTP Origin Server .
1. Zulassen von MP4-Dateien ohne Erweiterung für die JIT-Konvertierung über die Konfiguration &quot;Config/MP4Only&quot;zu vod.xml hinzugefügt

### Fehlerbehebungen in Version 1.3.1 {#bug-fixes-included-in-release-1}

* 3759167 - Nicht alle SCTE35-Hinweise geben aufgrund einer Zeitstempelanomalie bei der Verpackung einen Verweis auf das Ausgabedarstellungsmanifest. Wenden Sie pts_Adjustment auf die SpliceTime in der Meldung TimeSignal von SpliceInfoSection in SCTE35 an.

### Bekannte Probleme in Version 1.3.1 {#known-issues-in-release}

* 3717039 - Wenn der Packager so konfiguriert ist, dass er DPI-einfache Modus-Hinweise erstellt, sollte er wirklich nach bestimmten Signaltypen suchen, wie z. B. nach Möglichkeiten zum Einfügen oder Platzieren von Splice und nur zur Konvertierung in einfache Modus-Hinweise. Andere Signaltypen wie Programmstart, Netzwerkstart usw. sollten ignoriert werden.

* 3718598 - Wenn der Origin Server für die Bereitstellung geschützter Inhalte mit HSM-Zugriff konfiguriert ist und der Backend LunaSA-Client eine häufige Kommunikation mit dem HSM-Modul durchführt

## Neue Funktionen in Primetime Streaming Server 1.3 (APRIL-Version) {#what-s-new-in-primetime-streaming-server-april-release}

Die Primetime-Version 1.3 bietet mehrere neue Funktionen rund um Streaming-Inhalte, bessere Benutzerfreundlichkeit und Sicherheit.

**Primetime-Streaming-Server als einheitliche Form von Live Packager und Herkunftsserver**

Primetime Live Packager und Primetime Origin werden zusammengeführt, um als eine Komponente zu funktionieren. Diese Komponente kann als Packager oder als Ursprung verwendet werden oder die kombinierten Funktionen verwenden, um einen Live-Stream zu verpacken und zu hosten.

Dies bietet eine einheitliche Dateischnittstelle für diese Server, die die Ausführung auf einem einzigen Computer erleichtert. Es bietet weiterhin die Flexibilität, als separater Packager oder Origin konfiguriert zu werden.

**Beta MPEG- DASH-Unterstützung**

Primetime Streaming Server unterstützt MPEG-DASH-Verpackungen für Live- und VOD-Workflows. Die Live-Paketkomponente konvertiert eingehende RTMP- oder MPEG-2-TS-Streams in das DASH-Format. Die Origin-Komponente akzeptiert einen DASH-Stream.

Bei VOD-Workflows konvertiert die Komponente Offline Packager MP4- und TS-Assets in das ISOBFF-Format MPEG-DASH.

**Live-to-VOD-Konversion**

Eine neue Komponente Recording Server ist jetzt verfügbar, die die Erfassung eines Live-Streams und die Archivierung für die VOD-Wiedergabe unterstützt. Es unterstützt die Erstellung von vollständigen Wiederholungen von Ereignissen sowie Clips/Highlights für einen Teil des Ereignisses. Es kann so konfiguriert werden, dass nur Audio-Streams aufgezeichnet, Anzeigen entfernt oder in Live-Inhalten aufgenommen werden. Recording Server funktioniert mit Primetime Streaming Server sowie mit Drittanbieterursprüngen.

**Konvertierung von RTMP zu HLS in Primetime Live Packager**

Die Primetime Live Packager-Komponente unterstützt die Erstellung von HLS-Streams aus RTMP-Streams. Außerdem können Primetime DRM und Protected Streaming zu den HLS-Ausgabestreams hinzugefügt werden.

**Authentifizierung für eingehende RTMP-Streams an Primetime Live Packager**

Eine usermgmt.jar wird jetzt mit Primetime Live Packager bereitgestellt, um den Zugriff mit vertrauenswürdigen Anmeldedaten zu konfigurieren, wenn ein RTMP-Stream an Primetime Live Packager gesendet wird

Jetzt können die Kodierer so konfiguriert werden, dass beim Senden von Streams an Live Packager ein Benutzername/Kennwort verwendet wird.

**PlaylistCreator-Tool zum Erstellen von Manifesten auf oberster Ebene für HDS und HLS**

Mit dem Primetime Offline Packager ist jetzt ein Dienstprogramm PlaylistCreator.jar verfügbar, mit dem Sie mühelos Manifestdateien der obersten Ebene für HDS- und HLS-Assets erstellen können.

**Zusätzliche Sicherheitsfunktion zur Integration eines Hardware-Sicherheitsmoduls**

Primetime Offline Packager unterstützt jetzt den Zugriff auf das Paketberechtigungszertifikat und die allgemeinen Schlüssel über ein Hardware-Sicherheitsmodul.

Ein Hardware-Sicherheitsmodul bietet zusätzlichen Schutz für diese vertraulichen Assets.

**Verbesserte Leistung für VOD-Packaging**

Zur Verbesserung der Verpackungszeit für Mezzanin-Assets im Primetime Offline Packager wurden mehrere Leistungsverbesserungen eingeführt

**Verbesserte Leistung für JIT MP4-Packaging**

In die JIT-Paketfunktionen von Primetime Origin wurden verschiedene Leistungsverbesserungen integriert, um Benutzeranforderungen für eine große Bibliothek von VOD-Assets zu verarbeiten.

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### Mindestsystemanforderungen {#minimum-system-requirements}

**Netzanforderungen**

* Das Netzwerk sollte Multicast-fähig sein, um MPEG-TS-Streams von einem Kodierer an Live Packager zu senden. Live Packager akzeptiert auch einen RTMP-Stream von einem Kodierer, der kein Multicast-Netzwerk benötigt.

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder höher empfohlen)
* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)
* 1 Gbit Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)
* Datenträger:

   * (Disk-SAS) : Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD) : 400 MBit/s Lesen/Schreiben
   * (NAS) : 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java JRE 1.7 (Empfohlen: Sun/Oracle Hotspot JVM). Das JDK ist für JConsole-Zugriff auf die JMX-APIs erforderlich.

### Installieren und Konfigurieren von Primetime Streaming Server {#install-and-configure-primetime-streaming-server}

**Installieren des Streaming-Servers**

1. Laden Sie die Java SE- und JDK-Software aus dem [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) und folgen Sie den Installationsanweisungen.
2. Archivdatei Adobe Primetime-Streaming Server 1.4 extrahieren, `Primetime- StreamingServer-1-4-0-b206-12042014.zip` auf Ihre Festplatte.

**Starten des Primetime-Streaming-Servers**

Um den Streaming-Server zu starten, führen Sie den folgenden Befehl über die Befehlszeile im Stammverzeichnis des Streaming-Servers aus:\
`$./pss_start.sh`

**Konfigurieren des Primetime-Streaming-Servers als Live Packager oder HTTP Origin Server**

Um den Streaming-Server als Live Packager oder Herkunftsserver zu konfigurieren, aktualisieren Sie die Konfigurationsdatei pss.xml , die im Ordner &quot;conf&quot;im Stammverzeichnis des Streaming-Servers abgelegt ist:

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**Primetime-Streaming-Server beenden**

Um den Streaming-Server zu stoppen, führen Sie den folgenden Befehl im Stammverzeichnis des Streaming-Servers aus:\
`$./pss_stop.sh`

**Starten Sie den Primetime-Streaming-Server neu**

Um den Streaming-Server neu zu starten, beenden und starten Sie den Streaming-Server.

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Deinstallieren des Primetime-Streaming-Servers**

Um den Streaming-Server zu deinstallieren, beenden Sie den Streaming-Server und entfernen Sie den pss-Ordner des Streaming-Servers im Ordner &quot;Primetime&quot;

## Arbeiten mit Live Packager und Origin Server 1.4 {#working-with-live-packager-and-origin-server}

Dieser Abschnitt gilt, wenn Primetime Streaming Server nicht verwendet wird und stattdessen der Primetime Live Packager UND/ODER Primetime Origin Server bereitgestellt wird

### Mindestsystemanforderungen {#minimum-system-requirements-1}

**Netzanforderungen**

* Das Netzwerk sollte Multicast-fähig sein, um MPEG-TS-Streams von einem Kodierer an Live Packager zu senden. Live Packager akzeptiert auch einen RTMP-Stream von einem Kodierer, der kein Multicast-Netzwerk benötigt.

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder höher empfohlen)
* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)
* 1 Gbit Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)
* Datenträger:

   * (Disk-SAS) : Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD) : 400 MBit/s Lesen/Schreiben
   * (NAS) : 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java JRE 1.7 (Empfohlen: Sun/Oracle Hotspot JVM). Das JDK ist für JConsole-Zugriff auf die JMX-APIs erforderlich.

Die obigen Mindestsystemanforderungen gelten für Origin Server sowie Live Packager.

### Installieren und Konfigurieren von Live Packager {#install-and-configure-the-live-packager}

**Installieren des Live Packager**

1. Laden Sie die Java SE- und JDK-Software aus dem [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) und folgen Sie den Installationsanweisungen.
1. Archivdatei Adobe Primetime - Live Packager 1.4 extrahieren `Primetime-LivePackager-1-4-0-b206-12042014.zip` auf Ihre Festplatte.

**Installieren des HTTP Origin Servers**

1. Laden Sie die Java JRE- und JDK-Software aus dem [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) und folgen Sie den Installationsanweisungen.
1. Archivdatei Adobe Primetime - HTTP Origin Server 1.4 extrahieren, `Primetime-HttpOrigin-1-4-0-b206-12042014.zip`, auf Ihre Festplatte.

**Starten des Live Packager** Um den Packager zu starten, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Packager aus:\
`$packager_start.sh`

**Starten des HTTP-Ursprungs-Servers**

Führen Sie zum Starten des HTTP Origin Servers den folgenden Befehl über die Befehlszeile im Stammverzeichnis des Herkunftsservers aus:\
`$./origin_start.sh`

**Beenden Sie den Live Packager.**

Um den Packager zu stoppen, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Packager aus:\
`$packager_stop.sh`

**HTTP-Herkunftsserver beenden**

Um den HTTP-Herkunftsserver zu stoppen, führen Sie den folgenden Befehl im Stammverzeichnis des Herkunftsservers aus:\
`$./origin_stop.sh`

**Starten Sie den Live Packager neu**

Um den Packager neu zu starten, beenden und starten Sie den Packager.

**Hinweis**: Wenn der Packager gestartet wird, versucht er, die Bootstrap-Informationen aus dem Fragmentziel im temporären Ordner zu initialisieren. Wenn die Bootstrap-Informationen im Fragmentziel gefunden werden, bedeutet dies, dass der Packager neu gestartet wurde. Im Falle eines Neustart wartet der Packager bis zur nächsten Fragmentgrenze und beginnt dann mit der Verpackung. Der Packager fügt einen Lückeneintrag in den Bootstrap ein, um anzugeben, dass fehlende Fragmente vorhanden sind.

**Starten Sie den HTTP Origin Server neu**

Um den HTTP Origin Server neu zu starten, beenden und starten Sie den HTTP Origin Server.

**Live Packager konfigurieren**

Die Verteilungsdatei enthält eine Beispielkonfiguration, die zum Testen des Packager verwendet werden kann.

Nachdem Sie das Archiv Adobe Primetime - Live Packager 1.4 extrahiert haben, ändern Sie die Ordner in den Paketordner und führen Sie das Skript packager_start.sh aus. Die Beispielkonfiguration überwacht die Multicast-Adresse 239.235.0.3:14000 und führt den lokalen Herkunftsserver an Port 8080 aus. Die Ausgabe ist so konfiguriert, dass sie in die `packager/webroot/_default_/_default_/ directory`.

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**Konfigurieren des HTTP-Ursprungs-Servers**

Die hier verfügbaren Konfigurationsdetails finden Sie im Dokument Erste Schritte mit Primetime HTTP Origin Server .

**Deinstallieren von Live Packager**

Um den Packager zu deinstallieren, beenden Sie den Packager und entfernen Sie den Paketordner aus dem Ordner &quot;Primetime&quot;.

**Deinstallieren des HTTP Origin Servers**

Um den HTTP Origin Server zu deinstallieren, stoppen Sie den HTTP Origin Server und entfernen Sie den HTTPD-Ordner des HTTP Origin-Servers im Ordner &quot;Primetime&quot;.

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### Mindestsystemanforderungen {#minimum-system-requirements-2}

**Unterstützte Betriebssysteme**

* Linux CentOS 6.3 64 Bit

**Hardwareanforderungen**

* Intel® Pentium® 4 Prozessor mit 3,2 GHz (Intel Xeon® Dualcore oder höher empfohlen)
* 64-Bit-Betriebssysteme: 4 GB RAM (8 GB empfohlen)
* 1 Gbit Ethernet-Karte empfohlen (mehrere Netzwerkkarten und 10 Gbit werden ebenfalls unterstützt)
* Datenträger:

   * (Disk-SAS) : Mindestens 10 GB mit 7,5 K RPM
   * (Disk-SSD) : 400 MBit/s Lesen/Schreiben
   * (NAS) : 1 GB dedizierter Link

**Softwareanforderungen**

* Oracle Java JRE 1.7 oder höher.

### Installieren und Konfigurieren von Offline Packager {#install-and-configure-offline-packager}

Gehen Sie wie folgt vor, um Offline Packager zu installieren:

1. Laden Sie die Java SE-Software aus dem [Oracle-Site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) und befolgen Sie die Installationsanweisungen.
1. Archivdatei Adobe Primetime - Offline Packager 1.4 extrahieren, `Primetime- OfflinePackager-1-4-0-b206-12042014.zip`, auf Ihre Festplatte.

Die verfügbaren Konfigurationsdetails finden Sie im Dokument Erste Schritte mit Primetime Offline Packager . [here](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
