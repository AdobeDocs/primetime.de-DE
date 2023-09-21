---
description: Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten erkennt. Diese Möglichkeiten werden an den Content Resolver gesendet, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften der Platzierungsgelegenheiten und Metadaten personalisiert.
title: Opportunity-Generatoren und Content-Resolver
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Opportunity-Generatoren und Content-Resolver {#opportunity-generators-and-content-resolvers}

Ein Opportunitätsdetektor ist eine TVSDK-Komponente, die benutzerdefinierte Tags in einem Stream erkennt und Platzierungsmöglichkeiten erkennt. Diese Möglichkeiten werden an den Content Resolver gesendet, der den Inhalts-/Anzeigen-Einfüge-Workflow basierend auf den Eigenschaften der Platzierungsgelegenheiten und Metadaten personalisiert.

TVSDK enthält einen standardmäßigen Opportunity-Detektor:

* `PTOpportunityResolver`, der die standardmäßigen Anzeigencodes versteht

TVSDK enthält auch einen standardmäßigen Inhaltsauflöser, der Inhalte bereitstellt, die basierend auf dem Metadatenschlüssel im Player-Element eingefügt werden sollen:

* `PTContentResolver`

Sie können die standardmäßigen Opportunity-Detektoren und Content Resolver überschreiben, um den Werbe-Workflow wie folgt anzupassen:

* Unterstützung für benutzerdefinierte Tag-Erkennung hinzufügen
* Erkennen benutzerdefinierter Tags für das Einfügen von Anzeigen
* Erstellen eines benutzerdefinierten Anzeigenanbieters
* Schwarze Inhalte

<!--<a id="section_C2BA8F50230E4010ABFCD5D976BC1217"></a>-->

TVSDK bietet standardmäßige Opportunity-Generatoren und Content Resolver, die Anzeigen in der Timeline platzieren. Diese Generatoren und Resolver basieren auf nicht standardmäßigen Tags im Manifest. Ihre Anwendung muss die Timeline möglicherweise basierend auf den im Manifest identifizierten Möglichkeiten ändern, z. B. anhand von Indikatoren für einen Blackout-Zeitraum.

Ein *`opportunity`* stellt einen Zielpunkt auf der Timeline dar, der normalerweise auf eine Anzeigenplatzierungsmöglichkeit hinweist. Diese Möglichkeit kann auch einen benutzerdefinierten Vorgang angeben, der sich auf die Timeline auswirken kann, z. B. einen Abmeldezeitraum. Ein *`opportunity generator`* identifiziert spezifische Möglichkeiten (Tags) in der Zeitleiste und benachrichtigt TVSDK darüber, dass diese Möglichkeiten getaggt wurden. Chancen werden in einem Zeitrahmen unter `PTTimedMetadata` durch Einfügung eines nicht standardmäßigen (Nicht-HLS)-Tags.

Wenn Ihre Anwendung über eine Gelegenheit (Tag) benachrichtigt wird, kann Ihre Anwendung die Timeline ändern, indem Sie beispielsweise eine Reihe von Anzeigen einfügen, zu einem alternativen Stream (Blackouts) wechseln oder den Timeline-Inhalt anderweitig bearbeiten. Standardmäßig ruft TVSDK die entsprechende *`content resolver`* , um die erforderlichen Timeline-Änderungen oder -Aktionen zu implementieren. Ihre Anwendung kann den standardmäßigen TVSDK-Advertising Content Resolver verwenden oder einen eigenen Content Resolver registrieren.

Sie können auch `PTSDKConfig.setAdTags` , um weitere Anzeigenmarkierungen-Tags/-Hinweise hinzuzufügen, damit TVSDK sie erkennen und verwenden kann. `PTSDKConfig.setSubscribedTags` und benachrichtigen Sie Ihre Anwendung über zusätzliche Tags, die Informationen zum Werbe-Workflow enthalten könnten.

Eine mögliche Verwendung eines benutzerdefinierten Resolver ist für Blackout-Zeiträume. Um diese Zeiträume zu handhaben, könnte Ihre Anwendung einen Blackout-Opportunity-Detektor implementieren und registrieren, der für die Verarbeitung von Blackout-Tags zuständig ist. Wenn TVSDK auf dieses Tag trifft, fragt es alle registrierten Content Resolver ab, um den ersten zu finden, der das angegebene Tag verarbeitet. In diesem Beispiel handelt es sich um den Blackout-Inhaltsauflöser, der beispielsweise das aktuelle Element durch alternativen Inhalt im Player für die durch das Tag angegebene Dauer ersetzen kann.
