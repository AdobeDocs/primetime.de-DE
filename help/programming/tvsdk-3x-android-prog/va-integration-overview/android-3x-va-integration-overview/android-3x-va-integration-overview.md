---
description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-description: Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.
seo-title: Integration von TVSDK mit Adobe Analytics
title: Integration von TVSDK mit Adobe Analytics
uuid: 4d498d35-ec8e-40fc-8272-1637ef942bb0
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Integration von TVSDK mit Adobe Analytics {#integrating-tvsdk-with-adobe-analytics}

Sie können die Videonutzung verfolgen, indem Sie TVSDK mit Adobe Analytics integrieren.

Die Videoverfolgung in TVSDK verwendet den Dienst **Adobe Analytics Video Essentials**, der Videonutzungsmetriken bereitstellt, z. B. Ansichten, Videobeendigungen, Anzeigenimpressionen, Besuchszeit für Videos usw. Weitere Informationen zu diesem Dienst erhalten Sie von Ihrem Kundenbetreuer.

Im folgenden Verfahren werden die Schritte zur Aktivierung der Videoverfolgung im Player zusammengefasst:

1. Initialisieren und/oder konfigurieren Sie die folgenden Videoverfolgungskomponenten:

   >[!TIP]
   >
   >In Android sind diese Komponenten Teil von TVSDK.

   * JSON-Konfigurationsdatei
   * Videoanalysemetadatenobjekt
   * Globales Metadatenobjekt

1. Richten Sie den Berichte für Videoanalysen serverseitig mit den Adobe Analytics Admin Tools ein.