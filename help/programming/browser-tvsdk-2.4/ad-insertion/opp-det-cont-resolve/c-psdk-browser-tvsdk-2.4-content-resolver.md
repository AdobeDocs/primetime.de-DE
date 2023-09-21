---
description: Ein Opportunity-Detektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Content Resolver gesendet, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften der Platzierungsgelegenheiten und Metadaten personalisiert.
title: Anpassen von Opportunity-Detektoren und Content Resolver
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Übersicht {#customize-opportunity-detectors-and-content-resolvers-overview}

Ein Opportunity-Detektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Content Resolver gesendet, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften der Platzierungsgelegenheiten und Metadaten personalisiert.

Browser TVSDK enthält die folgenden standardmäßigen Opportunity-Detektoren:

* `AdSignalingModeOpportunityGenerator`, wodurch anfängliche Anzeigenplatzierungsmöglichkeiten basierend auf dem Anzeigensignalisierungsmodus geschaffen werden.
* `ManifestCuesOpportunityGenerator`, wodurch sich aus jedem Splink-out-Tag Anzeigenplatzierungsmöglichkeiten ergeben.

Browser TVSDK enthält auch standardmäßige Content-Resolver, wie z. B. `AuditudeResolver`, der Inhalt bereitstellt, der basierend auf dem Metadatenschlüssel im Player-Element eingefügt wird. `AuditudeResolver` kann mit Adobe Primetime-Werbe-Entscheidungsservern kommunizieren und Werbeunterbrechungen zurückgeben, die platziert werden sollen.

Sie können die standardmäßigen Opportunity-Detektoren und Content Resolver überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* Unterstützung für benutzerdefinierte Tag-Erkennung hinzufügen
* Erkennen benutzerdefinierter Tags für das Einfügen von Anzeigen
* Erstellen eines benutzerdefinierten Anzeigenanbieters
