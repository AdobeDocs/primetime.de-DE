---
description: Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-description: Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-title: Opportunity-Generatoren und Content-Auflösungen
title: Opportunity-Generatoren und Content-Auflösungen
uuid: 593de6c0-042d-4a05-82d7-056a9a4500f3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Opportunity-Generatoren und Content-Auflösungen {#opportunity-generators-and-content-resolvers}

Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.

TVSDK enthält einen Standard-Opportunitätsdetektor:

* `SpliceOutPlacementOpportunityDetector`, der die Standard-Anzeigenbezeichnungen versteht

TVSDK enthält außerdem Standard-Content-Auflösungen, die Inhalte bereitstellen, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden sollen:

* `AuditudeResolver` for  `AUDITUDE_METADATA_KEY`, das in der Lage ist, mit Adobe Primetime-Werbeanzeigen-Entscheidungsservern (früher Auditude genannt) zu kommunizieren und Werbeunterbrechungen zurückzugeben, die platziert werden sollen.

* `MetadataResolver` for  `JSON_METADATA_KEY`

* `CustomAdMarkersContentResolver` for  `TIME_RANGES_METADATA_KEY`

Sie können die standardmäßigen Opportunitätsdetektoren und Inhaltsauflöser überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* hinzufügen Unterstützung der benutzerdefinierten Tag-Erkennung
* Erkennen benutzerdefinierter Tags für die Anzeigeneinfügung
* Erstellen eines benutzerdefinierten Anzeigenanbieters
* Schwarzer Inhalt

TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren, und diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.

Ein *`opportunity`* stellt einen Interessensort auf der Zeitschiene dar, der normalerweise auf eine Anzeigenplatzierungsmöglichkeit hinweist. Diese Gelegenheit kann auch einen benutzerdefinierten Vorgang anzeigen, der sich auf die Zeitschiene auswirken kann, z. B. einen Sperrzeitraum. Ein *`opportunity generator`* identifiziert bestimmte Möglichkeiten (Tags) in der Zeitleiste und benachrichtigt TVSDK, dass diese Möglichkeiten getaggt wurden. Chancen werden in einer Zeitschiene durch Einfügen eines nicht standardmäßigen Tags (Nicht-HLS) identifiziert.

Wenn Ihre Anwendung über eine Gelegenheit (Tag) benachrichtigt wird, kann Ihre Anwendung die Zeitschiene ändern, indem Sie z. B. eine Reihe von Anzeigen einfügen, zu einem alternativen Stream (Blackouts) wechseln oder den Inhalt der Zeitschiene anderweitig bearbeiten. TVSDK ruft standardmäßig das entsprechende *`content resolver`* auf, um die erforderlichen Änderungen oder Aktionen in der Zeitschiene zu implementieren. Ihre Anwendung kann den standardmäßigen TVSDK Advertisement Content-Auflöser verwenden oder einen eigenen Content-Auflöser registrieren.

Sie können `MediaPlayerItemConfig.setAdTags` auch verwenden, um weitere Anzeigenmarken-Tags/Hinweise hinzuzufügen, damit TVSDK `MediaPlayerItemConfig.subscribedTags` erkennen und verwenden kann, und Ihre Anwendung über zusätzliche Tags benachrichtigen kann, die möglicherweise Informationen zum Anzeigenarbeitsablauf enthalten.

Eine mögliche Verwendung eines benutzerdefinierten Auflösers ist für Blackout-Zeiträume. Um diese Zeiträume zu bearbeiten, könnte Ihre Anwendung einen Blackout-Opportunitätsdetektor implementieren und registrieren, der für die Handhabung von Blackout-Tags zuständig ist. Wenn TVSDK auf dieses Tag trifft, fragt es alle registrierten Content-Auflöser ab, um den ersten zu finden, der das angegebene Tag verarbeitet. In diesem Beispiel ist es der Blackout-Inhaltsauflöser, der beispielsweise das aktuelle Element durch alternativen Inhalt im Player für die vom Tag angegebene Dauer ersetzen kann.
