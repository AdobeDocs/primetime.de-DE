---
description: Ein Opportunitätsgenerator identifiziert Platzierungsmöglichkeiten durch benutzerdefinierte Tags in einem Stream, benutzerdefinierte Anzeigensignalisierungsmodi usw. Der Opportunitätsgenerator sendet diese Platzierungsmöglichkeiten an den Content-Auflöser, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsmöglichkeit anpasst.
seo-description: Ein Opportunitätsgenerator identifiziert Platzierungsmöglichkeiten durch benutzerdefinierte Tags in einem Stream, benutzerdefinierte Anzeigensignalisierungsmodi usw. Der Opportunitätsgenerator sendet diese Platzierungsmöglichkeiten an den Content-Auflöser, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsmöglichkeit anpasst.
seo-title: Anpassen von Opportunitätserzeugern und Inhaltsauflösungen
title: Anpassen von Opportunitätserzeugern und Inhaltsauflösungen
uuid: 97738b80-5cf8-494f-8811-449bceded220
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# Übersicht {#customize-opportunity-generators-and-content-resolvers-overview}

Ein Opportunitätsgenerator identifiziert Platzierungsmöglichkeiten durch benutzerdefinierte Tags in einem Stream, benutzerdefinierte Anzeigensignalisierungsmodi usw. Der Opportunitätsgenerator sendet diese Platzierungsmöglichkeiten an den Content-Auflöser, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsmöglichkeit anpasst.

TVSDK umfasst die folgenden standardmäßigen Opportunitätsgeneratoren:

* `ManifestCuesOpportunityGenerator` generiert Chancen aus den Standard-Anzeigenbezeichnungen (  `#EXT-X-CUE`).

* `AdSignalingModeOpportunityGenerator` generiert eine erste Möglichkeit für den angegebenen Anzeigensignalisierungsmodus. Dabei werden Hinweise oder zeitgesteuerte Metadaten ignoriert.
* `CustomMarkerOpportunityGenerator` bietet Möglichkeiten zum Ersetzen von Back-In-C3-Anzeigen.
* `AuditudeResolver`&#39;s Opportunitätsgenerator erzeugt Chancen, wenn verzögertes und Auflösen eingeschaltet ist.

TVSDK enthält auch Standard-Inhaltsauflöser:

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`, der mit Primetime-Anzeigenentscheidungen kommunizieren kann.

Sie können die standardmäßigen Opportunitätserzeuger und Inhaltsauflöser außer Kraft setzen, um den Werbearbeitsablauf wie folgt anzupassen:

* Erkennen benutzerdefinierter Tags für die Anzeigeneinfügung
* Erstellen Sie einen benutzerdefinierten Anzeigenanbieter.
* Inhalt schwarz ausblenden.