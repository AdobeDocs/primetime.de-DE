---
description: Diese Klassen helfen dabei, Möglichkeiten in einer Zeitschiene für die Platzierung von Inhalten wie Anzeigen zu erkennen.
seo-description: Diese Klassen helfen dabei, Möglichkeiten in einer Zeitschiene für die Platzierung von Inhalten wie Anzeigen zu erkennen.
seo-title: Zeitleistengeneratoren-Klassen
title: Zeitleistengeneratoren-Klassen
uuid: 1e36b738-0684-44f0-b3c3-dd656c70f705
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Zeitgeneratorklassen{#timeline-generators-classes}

Diese Klassen helfen dabei, Möglichkeiten in einer Zeitschiene für die Platzierung von Inhalten wie Anzeigen zu erkennen.

Paket: [com.adobe.mediacore.timeline.generator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/package-detail.html)

| Name | Beschreibung |
|---|---|
| [AdSignalingModeOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/AdSignalingModeOpportunityGenerator.html) | Klasse, die eine anfängliche Chance für den angegebenen Anzeigensignalisierungsmodus schafft. |
| [OpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGenerator.html) | Basisklasse für alle Opportunitätsgeneratoren. |
| [OpportunityGeneratorClient](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGeneratorClient.html) | Schnittstelle verwendet von Opportunitätserzeugern zur Kommunikation mit TVSDK-Komponenten. |
| [SpliceOutOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/SpliceOutOpportunityGenerator.html) | Klasse, die die Wiedergabe-Timeline überwacht und in das Manifest eingefügte Anzeigenplatzierungsmöglichkeiten als SpliceOut-Kommentare erkennt. |
| [TimedMetadataOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/TimedMetadataOpportunityGenerator.html) | Standardimplementierung eines Opportunitätsgenerators, der zeitgesteuerte Metadateninformationen verwendet, um Werbemöglichkeiten zu erkennen und zu generieren. |