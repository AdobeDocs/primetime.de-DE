---
description: Ein Opportunity-Generator identifiziert Platzierungsmöglichkeiten durch benutzerdefinierte Tags in einem Stream, benutzerdefinierte Anzeigensignalisierungsmodusmarken usw. Der Opportunity-Generator sendet diese Platzierungsmöglichkeiten an den Content Resolver, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften und Metadaten der Platzierungsmöglichkeit personalisiert.
title: Anpassen von Opportunity-Generatoren und Content Resolvers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Übersicht {#customize-opportunity-generators-and-content-resolvers-overview}

Ein Opportunity-Generator identifiziert Platzierungsmöglichkeiten durch benutzerdefinierte Tags in einem Stream, benutzerdefinierte Anzeigensignalisierungsmodusmarken usw. Der Opportunity-Generator sendet diese Platzierungsmöglichkeiten an den Content Resolver, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften und Metadaten der Platzierungsmöglichkeit personalisiert.

TVSDK enthält die folgenden standardmäßigen Opportunity-Generatoren:

* `ManifestCuesOpportunityGenerator` generiert Chancen aus den Standard-AnzeigenHinweisen ( `#EXT-X-CUE`).

* `AdSignalingModeOpportunityGenerator` generiert eine erste Chance für den angegebenen Anzeigensignalmodus. Dabei werden Hinweise oder zeitgesteuerte Metadateninformationen ignoriert.
* `CustomMarkerOpportunityGenerator` generiert Möglichkeiten, um integrierte C3-Anzeigen zu ersetzen.
* `AuditudeResolver`Der Opportunity-Generator bietet Chancen, wenn die verzögerte Anzeigenauflösung aktiviert ist.

TVSDK enthält auch standardmäßige Inhaltsauflöser:

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`, der mit Primetime-Anzeigenentscheidungen kommunizieren kann.

Sie können die standardmäßigen Opportunity-Generatoren und Content Resolver überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* Erkennen benutzerdefinierter Tags für das Einfügen von Anzeigen
* Erstellen Sie einen benutzerdefinierten Anzeigenanbieter.
* Schwarze Inhalte.
