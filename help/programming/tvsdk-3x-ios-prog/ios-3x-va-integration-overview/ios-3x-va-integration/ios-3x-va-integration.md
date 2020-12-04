---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-title: Integration von Videoanalysen
title: Integration von Videoanalysen
uuid: 275d2c88-a15c-4645-9234-f29d32fc4a63
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Integration von Videoanalysen {#video-analytics-integration}

Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.

Die Videoverfolgung in TVSDK verwendet den Dienst **Adobe Analytics Video Essentials**, der Videonutzungsmetriken bereitstellt, z. B. Ansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Videos usw. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Kundenbetreuer.

Im folgenden Verfahren werden die Schritte zur Aktivierung der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   Unter iOS sind diese Komponenten Teil von TVSDK:

   * JSON-Konfigurationsdatei
   * Videoanalysemetadatenobjekt
   * Globales Metadatenobjekt
   * Videoanalysen-Verfolgungsobjekt

1. Richten Sie den Berichte für Videoanalysen serverseitig mit den Adobe Analytics Admin Tools ein.