---
description: Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-description: Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.
seo-title: Opportunity-Generatoren und Content-Auflösungen
title: Opportunity-Generatoren und Content-Auflösungen
uuid: c49494da-2145-40d7-8f4b-2ecaf2866ca4
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Opportunity-Generatoren und Content-Auflösungen {#opportunity-generators-and-content-resolvers}

Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten identifiziert. Diese Möglichkeiten werden an den Inhaltsauflöser gesendet, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsgelegenheit anpassen kann.

TVSDK enthält einen Standard-Opportunitätsdetektor:

* `PTOpportunityResolver`, der die Standard-Anzeigenbezeichnungen versteht

TVSDK enthält auch einen Standard-Content-Resolver, der Inhalte bereitstellt, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden:

* `PTContentResolver`

Sie können die standardmäßigen Opportunitätsdetektoren und Inhaltsauflöser überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* Hinzufügen Unterstützung der benutzerdefinierten Tag-Erkennung
* Erkennen benutzerdefinierter Tags für die Anzeigeneinfügung
* Erstellen eines benutzerdefinierten Anzeigenanbieters
* Schwarzer Inhalt

<!--<a id="section_C2BA8F50230E4010ABFCD5D976BC1217"></a>-->

TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.

Ein *`opportunity`* Punkt, der auf der Zeitschiene interessant ist und normalerweise auf eine Werbeplatzierungsmöglichkeit hinweist. Diese Gelegenheit kann auch einen benutzerdefinierten Vorgang anzeigen, der sich auf die Zeitschiene auswirken kann, z. B. einen Sperrzeitraum. Ein *`opportunity generator`* identifiziert bestimmte Möglichkeiten (Tags) in der Zeitschiene und benachrichtigt TVSDK, dass diese Möglichkeiten getaggt wurden. Chancen werden in einer Zeitschiene durch `PTTimedMetadata` das Hinzufügen eines nicht standardmäßigen Tags (Nicht-HLS) identifiziert.

Wenn Ihre Anwendung über eine Gelegenheit (Tag) benachrichtigt wird, kann Ihre Anwendung die Zeitschiene ändern, indem Sie z. B. eine Reihe von Anzeigen einfügen, zu einem alternativen Stream (Blackouts) wechseln oder den Inhalt der Zeitschiene anderweitig bearbeiten. Standardmäßig ruft TVSDK die entsprechenden auf, *`content resolver`* um die erforderlichen Änderungen oder Aktionen in der Zeitschiene zu implementieren. Ihre Anwendung kann den standardmäßigen TVSDK Advertisement Content-Auflöser verwenden oder einen eigenen Content-Auflöser registrieren.

Sie können auch weitere Anzeigenmarken-Tags/Hinweise hinzufügen, damit TVSDK Ihre Anwendung erkennen und verwenden kann `PTSDKConfig.setAdTags` `PTSDKConfig.setSubscribedTags` und Sie über zusätzliche Tags informieren kann, die möglicherweise Informationen zum Werbearbeitsablauf enthalten.

Eine mögliche Verwendung eines benutzerdefinierten Auflösers ist für Blackout-Zeiträume. Um diese Zeiträume zu bearbeiten, könnte Ihre Anwendung einen Blackout-Opportunitätsdetektor implementieren und registrieren, der für die Handhabung von Blackout-Tags zuständig ist. Wenn TVSDK auf dieses Tag trifft, fragt es alle registrierten Content-Auflöser ab, um den ersten zu finden, der das angegebene Tag verarbeitet. In diesem Beispiel ist es der Blackout-Inhaltsauflöser, der beispielsweise das aktuelle Element durch alternativen Inhalt im Player für die vom Tag angegebene Dauer ersetzen kann.