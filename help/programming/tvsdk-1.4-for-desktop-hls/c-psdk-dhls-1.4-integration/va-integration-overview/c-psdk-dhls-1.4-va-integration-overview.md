---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
title: Videoanalyse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Videoanalysen{#video-analytics}

Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.

Die Videoverfolgung in TVSDK verwendet den Dienst **Adobe Analytics Video Essentials**, der Videonutzungsmetriken bereitstellt, z. B. Ansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Videos usw. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Kundenbetreuer.

Im folgenden Verfahren werden die Schritte zur Aktivierung der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   * **AppMeasurement-Bibliothek** : Enthält die Basislogik für die Datenerfassung auf niedriger Ebene. Hier werden die Video Heartbeat-Daten gesammelt und über das Netzwerk gesendet.
   * **Video Heartbeat Library** : Enthält die Core-Logik der Video-Heartbeat-Datenerfassung. Die Video Heartbeat Library greift auf eine Untergruppe der Bibliotheks-APIs zu.`AppMeasurement`

      >[!TIP]
      >
      >Ihre App interagiert nicht direkt mit dem Video Heartbeat-Code. Stattdessen verwendet die App TVSDK-APIs, um die Videoverfolgungsfunktionen Ihres Players zu konfigurieren.

   * **VisitorID-Bibliothek** : Identifiziert eindeutig Besucher der Webseite, auf der der Videoplayer gehostet wird.
   >[!IMPORTANT]
   >
   >Die integrierte Videoverfolgungsfunktion von TVSDK hängt von einer ordnungsgemäß konfigurierten `AppMeasurement`-Instanz ab. Bei den Verfolgungselementen wird davon ausgegangen, dass die `AppMeasurement`-Bibliothek bereits instanziiert und konfiguriert ist, bevor die Videoverfolgung konfiguriert und aktiviert wird. TVSDK-Videoverfolgungsfunktionen hängen von der Existenz einer voll funktionsfähigen und ordnungsgemäß konfigurierten Instanz der `AppMeasurement`-Bibliothek ab.

1. Richten Sie den Berichte für Videoanalysen serverseitig mit den Adobe Analytics Admin Tools ein.

