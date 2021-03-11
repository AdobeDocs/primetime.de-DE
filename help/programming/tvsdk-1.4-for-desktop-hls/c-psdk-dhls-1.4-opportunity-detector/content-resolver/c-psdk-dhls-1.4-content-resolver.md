---
description: Ein Opportunitätsdetektor ist eine TVADK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
title: Anpassen von Opportunitätsdetektoren und Inhaltsauflösungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Übersicht {#customize-opportunity-detectors-and-content-resolvers-overiew}

Ein Opportunitätsdetektor ist eine TVADK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.

TVSDK enthält standardmäßige Opportunitätsdetektoren:

* `SpliceOutOpportunityDetector`, der die Standard-Anzeigenbezeichnungen versteht
* `AdSignalingModeOpportunityGenerator`, der für die Schaffung von Möglichkeiten zur Erstplatzierung von Anzeigen auf der Grundlage des Anzeigensignalisierungsmodus verantwortlich ist
* `SpliceOutOpportunityGenerator`, der für die Erstellung von Anzeigenplatzierungsmöglichkeiten aus einem beliebigen #EXT-X-CUE-Tag verantwortlich ist

TVSDK enthält auch einen Standard-Content-Resolver, der Inhalte bereitstellt, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden:

* `AuditudeResolver`, die mit Adobe Primetime-Ad-Decision-Servern kommunizieren können (früher als Auditude bezeichnet) und die Platzierung von Werbeunterbrechungen zurückgeben.

Sie können die standardmäßigen Opportunitätsdetektoren und Inhaltsauflöser überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* hinzufügen Unterstützung der benutzerdefinierten Tag-Erkennung
* Erkennen benutzerdefinierter Tags für die Anzeigeneinfügung
* Erstellen eines benutzerdefinierten Anzeigenanbieters
* Schwarzer Inhalt

