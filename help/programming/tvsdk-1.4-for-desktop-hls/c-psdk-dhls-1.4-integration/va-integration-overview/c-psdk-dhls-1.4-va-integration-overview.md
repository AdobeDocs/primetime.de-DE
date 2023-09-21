---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK in Adobe Analytics integrieren.
title: Video-Analyse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Video-Analyse{#video-analytics}

Sie können die Videonutzung verfolgen, indem Sie TVSDK in Adobe Analytics integrieren.

Video-Tracking in TVSDK verwendet die **Adobe Analytics-Video-Grundlagen** -Dienst, der Videointeraktionsmetriken wie Videoansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Video usw. bereitstellt. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Adobe-Support-Mitarbeiter.

Im folgenden Verfahren werden die Schritte zum Aktivieren der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   * **AppMeasurement-Bibliothek** - Enthält die grundlegende Logik der Datenerfassung auf niedriger Ebene. Hier werden die Video Heartbeat-Daten gesammelt und über das Netzwerk gesendet.
   * **Video Heartbeat Library** - Enthält die Video-Heartbeat-Datenerfassungskernlogik. Die Video Heartbeat Library greift auf eine Untergruppe der `AppMeasurement` Bibliotheks-APIs.

     >[!TIP]
     >
     >Ihre App interagiert nicht direkt mit dem Video Heartbeat-Code. Stattdessen verwendet das Programm TVSDK-APIs, um die Video-Tracking-Funktionen Ihres Players zu konfigurieren.

   * **VisitorID Library** - Identifiziert eindeutig Besucher der Webseite, die als Host für den Videoplayer dient.

   >[!IMPORTANT]
   >
   >Die integrierte Video-Tracking-Funktion des TVSDK hängt von einer ordnungsgemäß konfigurierten ab `AppMeasurement` -Instanz. Die Tracking-Elemente setzen voraus, dass die Variable `AppMeasurement` -Bibliothek wurde bereits instanziiert und konfiguriert, bevor das Video-Tracking konfiguriert und aktiviert wurde. Die TVSDK-Video-Tracking-Funktionen hängen von der Existenz einer vollständig funktionierenden und ordnungsgemäß konfigurierten Instanz der `AppMeasurement` -Bibliothek.

1. Richten Sie die Videoanalyseberichte serverseitig mithilfe der Adobe Analytics Admin Tools ein.
