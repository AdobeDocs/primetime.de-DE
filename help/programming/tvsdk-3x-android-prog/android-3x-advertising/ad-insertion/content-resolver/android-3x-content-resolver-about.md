---
description: TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.
seo-description: TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.
seo-title: Opportunity-Generatoren und Content-Auflösungen
title: Opportunity-Generatoren und Content-Auflösungen
uuid: 5caf8924-3d76-45a1-a136-39932abe88b3
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Opportunity-Generatoren und Content-Auflösungen {#opportunity-generators-and-content-resolvers}

TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.

Ein *`opportunity`* Punkt, der auf der Zeitschiene interessant ist und normalerweise auf eine Werbeplatzierungsmöglichkeit hinweist. Diese Gelegenheit kann auch einen benutzerdefinierten Vorgang anzeigen, der sich auf die Zeitschiene auswirken kann, z. B. einen Sperrzeitraum. Ein *`opportunity generator`* identifiziert bestimmte Möglichkeiten (Tags) in der Zeitschiene und benachrichtigt TVSDK, dass diese Möglichkeiten getaggt wurden. Chancen werden in einer Zeitschiene durch Einfügen eines nicht standardmäßigen Tags (Nicht-HLS) identifiziert.

Wenn Ihre Anwendung über eine Gelegenheit benachrichtigt wird, kann Ihre Anwendung die Zeitschiene ändern, indem Sie eine Reihe von Anzeigen einfügen, zu einem alternativen Stream wechseln (Blackouts) oder den Inhalt der Zeitschiene anderweitig bearbeiten. Standardmäßig ruft TVSDK die entsprechenden auf, *`content resolver`* um die erforderlichen Änderungen oder Aktionen in der Zeitschiene zu implementieren. Ihre Anwendung kann den standardmäßigen TVSDK Advertisement Content-Auflöser verwenden oder einen eigenen Content-Auflöser registrieren.

Sie können auch weitere Anzeigenmarken-Tags/Hinweise hinzufügen, damit TVSDK Ihre Anwendung erkennen und verwenden kann `MediaPlayerItemConfig.setAdTags` `MediaPlayerItemConfig.subscribedTags` und Sie über zusätzliche Tags informieren kann, die möglicherweise Informationen zum Werbe-Workflow enthalten.

Eine mögliche Verwendung eines benutzerdefinierten Auflösers ist für Blackout-Zeiträume. Um diese Zeiträume zu bearbeiten, könnte Ihre Anwendung einen Blackout-Opportunitätsdetektor implementieren und registrieren, der für die Handhabung von Blackout-Tags zuständig ist. Wenn TVSDK auf dieses Tag trifft, fragt es alle registrierten Content-Auflöser ab, um den ersten zu finden, der das angegebene Tag verarbeitet. In diesem Beispiel ist es der Blackout-Inhaltsauflöser, der beispielsweise das aktuelle Element durch alternativen Inhalt im Player für die vom Tag angegebene Dauer ersetzen kann.