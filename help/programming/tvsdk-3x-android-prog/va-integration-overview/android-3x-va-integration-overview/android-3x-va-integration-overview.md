---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-title: Integration von TVSDK mit Adobe Analytics
title: Integration von TVSDK mit Adobe Analytics
uuid: 4d498d35-ec8e-40fc-8272-1637ef942bb0
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Integration von TVSDK mit Adobe Analytics {#integrating-tvsdk-with-adobe-analytics}

Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.

Die Videoverfolgung in TVSDK verwendet den **Adobe Analytics Video Essentials** -Dienst, der Videointeraktionsmetriken wie Video-Ansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Videos usw. bereitstellt. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Adobe-Kundenbetreuer.

Im folgenden Verfahren werden die Schritte zur Aktivierung der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   >[!TIP]
   >
   >In Android sind diese Komponenten Teil von TVSDK.

   * JSON-Konfigurationsdatei
   * Videoanalysemetadatenobjekt
   * Globales Metadatenobjekt

1. Richten Sie den Berichte für Videoanalysen serverseitig mit den Adobe Analytics Admin Tools ein.