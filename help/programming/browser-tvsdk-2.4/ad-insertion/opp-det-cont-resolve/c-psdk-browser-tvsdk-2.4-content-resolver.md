---
description: Ein Opportunitätsdetektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-description: Ein Opportunitätsdetektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-title: Anpassen von Opportunitätsdetektoren und Inhaltsauflösungen
title: Anpassen von Opportunitätsdetektoren und Inhaltsauflösungen
uuid: d4926933-5966-4cd8-8050-c81c5e3c8545
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Übersicht {#customize-opportunity-detectors-and-content-resolvers-overview}

Ein Opportunitätsdetektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.

Browser TVSDK enthält die folgenden standardmäßigen Opportunitätsdetektoren:

* `AdSignalingModeOpportunityGenerator`, was anfängliche Anzeigenplatzierungsmöglichkeiten auf Grundlage des Anzeigensignalisierungsmodus schafft.
* `ManifestCuesOpportunityGenerator`, wodurch sich aus jedem Splice-out-Tag Anzeigenplatzierungsmöglichkeiten ergeben.

Browser TVSDK enthält auch standardmäßige Inhaltsauflöser, wie `AuditudeResolver`zum Beispiel, die Inhalte bereitstellen, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden. `AuditudeResolver` kann mit Adobe Primetime-Werbeanzeigen-Entscheidungsservern kommunizieren und Werbeunterbrechungen zurückgeben, die platziert werden sollen.

Sie können die standardmäßigen Opportunitätsdetektoren und Inhaltsauflöser überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* Hinzufügen Unterstützung der benutzerdefinierten Tag-Erkennung
* Erkennen benutzerdefinierter Tags für die Anzeigeneinfügung
* Erstellen eines benutzerdefinierten Anzeigenanbieters

