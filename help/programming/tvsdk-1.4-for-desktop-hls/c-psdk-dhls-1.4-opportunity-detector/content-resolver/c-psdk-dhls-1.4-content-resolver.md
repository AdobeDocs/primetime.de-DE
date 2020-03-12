---
description: Ein Opportunitätsdetektor ist eine TVADK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-description: Ein Opportunitätsdetektor ist eine TVADK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-title: Anpassen von Opportunitätsdetektoren und Inhaltsauflösungen
title: Anpassen von Opportunitätsdetektoren und Inhaltsauflösungen
uuid: 7bd04c8f-6f04-4321-88e8-9bb93251d940
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Übersicht {#customize-opportunity-detectors-and-content-resolvers-overiew}

Ein Opportunitätsdetektor ist eine TVADK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.

TVSDK enthält standardmäßige Opportunitätsdetektoren:

* `SpliceOutOpportunityDetector`, der die Standard-Anzeigenbezeichnungen versteht
* `AdSignalingModeOpportunityGenerator`, der für die Schaffung von Möglichkeiten zur Erstplatzierung von Anzeigen auf der Grundlage des Anzeigensignalisierungsmodus verantwortlich ist
* `SpliceOutOpportunityGenerator`, der für die Erstellung von Anzeigenplatzierungsmöglichkeiten aus einem beliebigen #EXT-X-CUE-Tag verantwortlich ist

TVSDK enthält auch einen Standard-Content-Resolver, der Inhalte bereitstellt, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden:

* `AuditudeResolver`, die mit Adobe Primetime-Werbeanzeigen-Entscheidungsservern kommunizieren können (früher Auditude genannt) und die Platzierung von Werbeunterbrechungen zurückgeben.

Sie können die standardmäßigen Opportunitätsdetektoren und Inhaltsauflöser überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* Hinzufügen Unterstützung der benutzerdefinierten Tag-Erkennung
* Erkennen benutzerdefinierter Tags für die Anzeigeneinfügung
* Erstellen eines benutzerdefinierten Anzeigenanbieters
* Schwarzer Inhalt

