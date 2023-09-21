---
description: Diese Klassen helfen bei der Erkennung von Möglichkeiten in einer Zeitleiste für die Platzierung von Inhalten, z. B. Anzeigen.
title: Timeline-Generatorklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Timeline-Generatorklassen{#timeline-generators-classes}

Diese Klassen helfen bei der Erkennung von Möglichkeiten in einer Zeitleiste für die Platzierung von Inhalten, z. B. Anzeigen.

Package: [com.adobe.mediacore.timeline.generators](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/package-detail.html)

| Name | Beschreibung |
|---|---|
| [AdSignalingModeOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/AdSignalingModeOpportunityGenerator.html) | Klasse, die eine anfängliche Chance für den angegebenen Werbesignalmodus schafft. |
| [ChancenGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGenerator.html) | Basisklasse für alle Opportunity-Generatoren. |
| [OpportunityGeneratorClient](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGeneratorClient.html) | Schnittstelle, die von Opportunity-Generatoren zur Kommunikation mit TVSDK-Komponenten verwendet wird. |
| [SpliceOutOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/SpliceOutOpportunityGenerator.html) | Klasse, die die Wiedergabe-Timeline überwacht und in das Manifest eingefügte Anzeigenplatzierungsmöglichkeiten als SpliceOut-Kommentare erkennt. |
| [TimedMetadataOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/TimedMetadataOpportunityGenerator.html) | Standardimplementierung eines Opportunity-Generators, der zeitgesteuerte Metadateninformationen verwendet, um Werbemöglichkeiten zu erkennen und zu generieren. |
