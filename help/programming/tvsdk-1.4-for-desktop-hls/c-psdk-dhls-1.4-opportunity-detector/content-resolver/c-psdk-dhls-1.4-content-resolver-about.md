---
description: TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren, und diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.
title: Opportunity-Generatoren und Content-Auflösungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Opportunity-Generatoren und Content-Auflöser{#opportunity-generators-and-content-resolvers}

TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren, und diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest festgelegten Möglichkeiten, wie z. B. Indikatoren für eine Sperrfrist, ändern.

Ein *`opportunity`* stellt einen Interessensort auf der Zeitschiene dar, der normalerweise auf eine Anzeigenplatzierungsmöglichkeit hinweist. Diese Gelegenheit kann auch einen benutzerdefinierten Vorgang anzeigen, der sich auf die Zeitschiene auswirken kann, z. B. einen Sperrzeitraum. Ein *`opportunity generator`* identifiziert bestimmte Möglichkeiten (Tags) in der Zeitleiste und benachrichtigt TVSDK, dass diese Möglichkeiten getaggt wurden. Chancen werden in einer Zeitschiene in `TimedMetadata` identifiziert. Das `SpliceOutOpportunityGenerator` erstellt Chancen auf Grundlage der `TimedMetadata`-Objekte, die für jedes im Manifest erkannte Anzeigen-Tag erstellt wurden, und das `AdSignalingModeOpportunityGenerator` erstellt die anfängliche Gelegenheit, die auf dem `MediaPlayerItem`-Typ und dem zugehörigen Anzeigensignalisierungsmodus basiert.

Wenn Ihre Anwendung über eine Gelegenheit (Tag) benachrichtigt wird, kann Ihre Anwendung die Zeitschiene ändern, indem Sie z. B. eine Reihe von Anzeigen einfügen, zu einem alternativen Stream (Blackouts) wechseln oder den Inhalt der Zeitschiene anderweitig bearbeiten. TVSDK ruft standardmäßig das entsprechende *`content resolver`* auf, um die erforderlichen Änderungen oder Aktionen in der Zeitschiene zu implementieren. Ihre Anwendung kann den standardmäßigen TVSDK Advertisement Content-Auflöser verwenden oder einen eigenen Content-Auflöser registrieren.

Sie können `PSDKConfig.adTags` auch verwenden, um mehr Anzeigenmarken-Tags/Hinweise für die standardmäßige `SpliceOutOpportunityGenerator`-Klasse hinzuzufügen und `PSDKConfig.setSubscribedTags` zu verwenden, damit TVSDK Ihre Anwendung über zusätzliche Tags benachrichtigen kann, die möglicherweise Informationen zum Werbe-Workflow enthalten.

Eine mögliche Verwendung eines benutzerdefinierten Auflösers ist für Blackout-Zeiträume. Um diese Zeiträume zu bearbeiten, könnte Ihre Anwendung einen Blackout-Opportunitätsdetektor implementieren und registrieren, der für die Handhabung von Blackout-Tags zuständig ist. Wenn TVSDK auf dieses Tag trifft, fragt es alle registrierten Content-Auflöser ab, um den ersten zu finden, der das angegebene Tag verarbeitet. In diesem Beispiel ist es der Blackout-Inhaltsauflöser, der beispielsweise das aktuelle Element durch alternativen Inhalt im Player für die vom Tag angegebene Dauer ersetzen kann.
