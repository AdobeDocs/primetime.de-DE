---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-title: Videoanalyse
title: Videoanalyse
uuid: c3cb0574-1117-409c-8aa7-641363d8d85f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Videoanalyse{#video-analytics}

Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.

Die Videoverfolgung in TVSDK verwendet den **Adobe Analytics Video Essentials** -Dienst, der Videointeraktionsmetriken wie Video-Ansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Videos usw. bereitstellt. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Adobe-Kundenbetreuer.

Im folgenden Verfahren werden die Schritte zur Aktivierung der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   * **AppMeasurement-Bibliothek** : Enthält die Basislogik für die Datenerfassung auf niedriger Ebene. Hier werden die Video Heartbeat-Daten gesammelt und über das Netzwerk gesendet.
   * **Video Heartbeat Library** - Enthält die Core-Logik der Video-Heartbeat-Datenerfassung. Die Video Heartbeat Library greift auf eine Untergruppe der `AppMeasurement` Bibliotheks-APIs zu.

      >[!TIP]
      >
      >Ihre App interagiert nicht direkt mit dem Video Heartbeat-Code. Stattdessen verwendet die App TVSDK-APIs, um die Videoverfolgungsfunktionen Ihres Players zu konfigurieren.

   * **VisitorID-Bibliothek** : Identifiziert eindeutig Besucher der Webseite, auf der der Videoplayer gehostet wird.
   >[!IMPORTANT]
   >
   >Die integrierte Videoverfolgungsfunktion von TVSDK hängt von einer ordnungsgemäß konfigurierten `AppMeasurement` Instanz ab. Bei den Verfolgungselementen wird davon ausgegangen, dass die `AppMeasurement` Bibliothek bereits instanziiert und konfiguriert ist, bevor die Videoverfolgung konfiguriert und aktiviert wird. TVSDK-Videoverfolgungsfunktionen hängen von der Existenz einer voll funktionsfähigen und ordnungsgemäß konfigurierten Instanz der `AppMeasurement` Bibliothek ab.

1. Richten Sie den Berichte für Videoanalysen serverseitig mit den Adobe Analytics Admin Tools ein.

