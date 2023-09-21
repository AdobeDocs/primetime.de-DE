---
description: Sie können die Videonutzung verfolgen, indem Sie Browser TVSDK in Adobe Analytics integrieren.
title: Video-Analyse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Video-Analyse{#video-analytics}

Sie können die Videonutzung verfolgen, indem Sie Browser TVSDK in Adobe Analytics integrieren.

Video-Tracking in Browser TVSDK verwendet die **Adobe Analytics-Video-Grundlagen** -Dienst, der Videointeraktionsmetriken wie Videoansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Video usw. bereitstellt. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Adobe-Support-Mitarbeiter.

Im folgenden Verfahren werden die Schritte zum Aktivieren der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   * **AppMeasurement-Bibliothek** - Enthält die grundlegende Logik der Datenerfassung auf niedriger Ebene. Hier werden die Video Heartbeat-Daten gesammelt und über das Netzwerk gesendet.
   * **Video Heartbeat Library** - Enthält die Video-Heartbeat-Datenerfassungskernlogik. Die Video Heartbeat Library greift auf eine Untergruppe der AppMeasurement Library-APIs zu.

     >[!TIP]
     >
     >Ihre App interagiert nicht direkt mit dem Video Heartbeat-Code. Stattdessen verwendet das Programm Browser TVSDK-APIs, um die Video-Tracking-Funktionen Ihres Players zu konfigurieren.

   * **VisitorID Library** - Identifiziert eindeutig Besucher der Webseite, die als Host für den Videoplayer dient.

   >[!IMPORTANT]
   >
   >Die integrierte Videoverfolgungsfunktion von Browser TVSDK hängt von einer ordnungsgemäß konfigurierten AppMeasurement-Instanz ab. Bei den Tracking-Elementen wird davon ausgegangen, dass die AppMeasurement-Bibliothek bereits instanziiert und konfiguriert ist, bevor die Videoverfolgung konfiguriert und aktiviert wird. Die Video-Tracking-Funktionen des Browser-TVSDK hängen von der Existenz einer vollständig funktionierenden und ordnungsgemäß konfigurierten Instanz der AppMeasurement-Bibliothek ab.

1. Richten Sie die Videoanalyseberichte serverseitig mithilfe der Adobe Analytics Admin Tools ein.
