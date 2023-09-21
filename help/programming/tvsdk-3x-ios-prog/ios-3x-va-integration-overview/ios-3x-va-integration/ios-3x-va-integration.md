---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK in Adobe Analytics integrieren.
title: Video Analytics-Integration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Video Analytics-Integration {#video-analytics-integration}

Sie können die Videonutzung verfolgen, indem Sie TVSDK in Adobe Analytics integrieren.

Video-Tracking in TVSDK verwendet die **Adobe Analytics-Video-Grundlagen** -Dienst, der Videointeraktionsmetriken wie Videoansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Video usw. bereitstellt. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Adobe-Support-Mitarbeiter.

Im folgenden Verfahren werden die Schritte zum Aktivieren der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   In iOS sind diese Komponenten Teil von TVSDK:

   * JSON-Konfigurationsdatei
   * Video Analytics-Metadatenobjekt
   * Globales Metadatenobjekt
   * Video Analytics-Tracker-Objekt

1. Richten Sie die Videoanalyseberichte serverseitig mithilfe der Adobe Analytics Admin Tools ein.
