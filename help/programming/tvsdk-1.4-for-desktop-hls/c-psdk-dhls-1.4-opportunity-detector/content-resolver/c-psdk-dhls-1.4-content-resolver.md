---
description: Ein Opportunitätsdetektor ist eine TVADK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten erkennt. Diese Möglichkeiten werden an den Content Resolver gesendet, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften der Platzierungsgelegenheiten und Metadaten personalisiert.
title: Anpassen von Opportunity-Detektoren und Content Resolver
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Übersicht {#customize-opportunity-detectors-and-content-resolvers-overiew}

Ein Opportunitätsdetektor ist eine TVADK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten erkennt. Diese Möglichkeiten werden an den Content Resolver gesendet, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften der Platzierungsgelegenheiten und Metadaten personalisiert.

TVSDK enthält standardmäßige Opportunitätsdetektoren:

* `SpliceOutOpportunityDetector`, der die standardmäßigen Anzeigencodes versteht
* `AdSignalingModeOpportunityGenerator`, der für die Erstellung von Platzierungsmöglichkeiten für erste Anzeigen basierend auf dem Anzeigensignalisierungsmodus verantwortlich ist
* `SpliceOutOpportunityGenerator`, der für die Erstellung von Anzeigenplatzierungsmöglichkeiten über ein beliebiges #EXT-X-CUE -Tag verantwortlich ist

TVSDK enthält auch einen standardmäßigen Inhaltsauflöser, der Inhalte bereitstellt, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden sollen:

* `AuditudeResolver`, kann mit Adobe Primetime-Werbe-Entscheidungsservern (früher als Auditude bezeichnet) kommunizieren und gibt Werbeunterbrechungen zurück, die platziert werden sollen.

Sie können die standardmäßigen Opportunity-Detektoren und Content Resolver überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* Unterstützung für benutzerdefinierte Tag-Erkennung hinzufügen
* Erkennen benutzerdefinierter Tags für das Einfügen von Anzeigen
* Erstellen eines benutzerdefinierten Anzeigenanbieters
* Schwarze Inhalte
