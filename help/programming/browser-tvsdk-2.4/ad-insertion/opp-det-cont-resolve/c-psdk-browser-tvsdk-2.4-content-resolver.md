---
description: Ein Opportunitätsdetektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-description: Ein Opportunitätsdetektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-title: Anpassen von Opportunitätsdetektoren und Inhaltsauflösungen
title: Anpassen von Opportunitätsdetektoren und Inhaltsauflösungen
uuid: d4926933-5966-4cd8-8050-c81c5e3c8545
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---


# Übersicht {#customize-opportunity-detectors-and-content-resolvers-overview}

Ein Opportunitätsdetektor ist eine Browser TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.

Browser TVSDK enthält die folgenden standardmäßigen Opportunitätsdetektoren:

* `AdSignalingModeOpportunityGenerator`, was anfängliche Anzeigenplatzierungsmöglichkeiten auf Grundlage des Anzeigensignalisierungsmodus schafft.
* `ManifestCuesOpportunityGenerator`, wodurch sich aus jedem Splice-out-Tag Anzeigenplatzierungsmöglichkeiten ergeben.

Browser TVSDK enthält auch Standard-Inhaltsauflöser, wie `AuditudeResolver`, die Inhalte bereitstellen, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden. `AuditudeResolver` ist in der Lage, mit den Adobe Primetime-Werbeanzeigen-Entscheidungsservern zu kommunizieren und Werbeunterbrechungen zurückzugeben, die platziert werden sollen.

Sie können die standardmäßigen Opportunitätsdetektoren und Inhaltsauflöser überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* hinzufügen Unterstützung der benutzerdefinierten Tag-Erkennung
* Erkennen benutzerdefinierter Tags für die Anzeigeneinfügung
* Erstellen eines benutzerdefinierten Anzeigenanbieters

