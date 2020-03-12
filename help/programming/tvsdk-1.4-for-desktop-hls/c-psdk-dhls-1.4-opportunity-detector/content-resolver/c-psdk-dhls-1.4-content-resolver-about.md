---
description: TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.
seo-description: TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.
seo-title: Opportunity-Generatoren und Content-Auflösungen
title: Opportunity-Generatoren und Content-Auflösungen
uuid: 9eaeeacf-9e7c-4ebb-a91e-fbc53e96d2c3
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Opportunity-Generatoren und Content-Auflösungen{#opportunity-generators-and-content-resolvers}

TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.

Ein *`opportunity`* Punkt, der auf der Zeitschiene interessant ist und normalerweise auf eine Werbeplatzierungsmöglichkeit hinweist. Diese Gelegenheit kann auch einen benutzerdefinierten Vorgang anzeigen, der sich auf die Zeitschiene auswirken kann, z. B. einen Sperrzeitraum. Ein *`opportunity generator`* identifiziert bestimmte Möglichkeiten (Tags) in der Zeitschiene und benachrichtigt TVSDK, dass diese Möglichkeiten getaggt wurden. Chancen werden in einem Zeitplan in `TimedMetadata`aufgeführt. Die Funktion `SpliceOutOpportunityGenerator` bietet Möglichkeiten basierend auf den `TimedMetadata` Objekten, die für jedes im Manifest erkannte Anzeigen-Tag erstellt wurden, und `AdSignalingModeOpportunityGenerator` schafft die anfängliche Möglichkeit, die auf dem `MediaPlayerItem` Typ und dem zugehörigen Anzeigensignalisierungsmodus basiert.

Wenn Ihre Anwendung über eine Gelegenheit (Tag) benachrichtigt wird, kann Ihre Anwendung die Zeitschiene ändern, indem Sie z. B. eine Reihe von Anzeigen einfügen, zu einem alternativen Stream (Blackouts) wechseln oder den Inhalt der Zeitschiene anderweitig bearbeiten. Standardmäßig ruft TVSDK die entsprechenden auf, *`content resolver`* um die erforderlichen Änderungen oder Aktionen in der Zeitschiene zu implementieren. Ihre Anwendung kann den standardmäßigen TVSDK Advertisement Content-Auflöser verwenden oder einen eigenen Content-Auflöser registrieren.

Sie können auch mehr Anzeigenmarken-Tags/Hinweise für die Standard- `PSDKConfig.adTags` Klasse hinzufügen und verwenden, `SpliceOutOpportunityGenerator` `PSDKConfig.setSubscribedTags` damit TVSDK Ihre Anwendung über zusätzliche Tags benachrichtigen kann, die möglicherweise Informationen zum Anzeigen-Workflow enthalten.

Eine mögliche Verwendung eines benutzerdefinierten Auflösers ist für Blackout-Zeiträume. Um diese Zeiträume zu bearbeiten, könnte Ihre Anwendung einen Blackout-Opportunitätsdetektor implementieren und registrieren, der für die Handhabung von Blackout-Tags zuständig ist. Wenn TVSDK auf dieses Tag trifft, fragt es alle registrierten Content-Auflöser ab, um den ersten zu finden, der das angegebene Tag verarbeitet. In diesem Beispiel ist es der Blackout-Inhaltsauflöser, der beispielsweise das aktuelle Element durch alternativen Inhalt im Player für die vom Tag angegebene Dauer ersetzen kann.
