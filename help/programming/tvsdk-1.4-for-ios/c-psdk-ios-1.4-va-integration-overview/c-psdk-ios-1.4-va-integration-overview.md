---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-title: Videoanalyse
title: Videoanalyse
uuid: 8f297316-f95e-4896-b489-a2d6b36e6b40
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Integration von Videoanalysen {#video-analytics-integration}

Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.

Die Videoverfolgung in TVSDK verwendet den **Adobe Analytics Video Essentials** -Dienst, der Videointeraktionsmetriken wie Video-Ansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Videos usw. bereitstellt. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Adobe-Kundenbetreuer.

Im folgenden Verfahren werden die Schritte zur Aktivierung der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   Unter iOS sind diese Komponenten Teil von TVSDK:

   * JSON-Konfigurationsdatei
   * Videoanalysemetadatenobjekt
   * Globales Metadatenobjekt
   * Videoanalysen-Verfolgungsobjekt

1. Richten Sie den Berichte für Videoanalysen serverseitig mit den Adobe Analytics Admin Tools ein.