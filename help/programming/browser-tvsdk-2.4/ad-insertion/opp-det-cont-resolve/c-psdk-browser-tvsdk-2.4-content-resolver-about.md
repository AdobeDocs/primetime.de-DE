---
description: Browser TVSDK bietet standardmäßige Opportunity-Generatoren und Content Resolver, die Anzeigen in der Timeline platzieren. Diese Generatoren und Resolver basieren auf nicht standardmäßigen Tags im Manifest. Ihre Anwendung muss die Timeline möglicherweise basierend auf den im Manifest identifizierten Möglichkeiten ändern.
title: Opportunity-Generatoren und Content-Resolver
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Opportunity-Generatoren und Content-Resolver{#opportunity-generators-and-content-resolvers}

Browser TVSDK bietet standardmäßige Opportunity-Generatoren und Content Resolver, die Anzeigen in der Timeline platzieren. Diese Generatoren und Resolver basieren auf nicht standardmäßigen Tags im Manifest. Ihre Anwendung muss die Timeline möglicherweise basierend auf den im Manifest identifizierten Möglichkeiten ändern.

Ein *`opportunity`* stellt einen Zielpunkt auf der Timeline dar, der normalerweise auf eine Anzeigenplatzierungsmöglichkeit hinweist. Diese Möglichkeit kann auch einen benutzerdefinierten Vorgang angeben, der sich auf die Timeline auswirken kann. Ein *`opportunity generator`* identifiziert spezifische Möglichkeiten (Tags) in der Zeitleiste und benachrichtigt TVSDK darüber, dass diese Möglichkeiten getaggt wurden.

Chancen werden in einem Zeitrahmen unter `TimedMetata`. Die `ManifestCuesOpportunityGenerator` schafft Chancen auf der Grundlage der `TimedMetadata` Objekte, die für jedes Anzeigen-Tag der Aufspaltung (in `MediaPlayerItemConfig.adTags`), die im Manifest erkannt wurde. Die `AdSignalingModeOpportunityGenerator` schafft die anfängliche Chance, die auf der `MediaPlayerItem` Typ und zugehörigen Anzeigensignalmodus.

>[!TIP]
>
>Wenn die Variable `AdvertisingMetadata.livePreroll` oder `AdvertisingMetadata.preroll` -Eigenschaft festgelegt ist, `AdSignalingModeOpportunityGenerator` generiert eine Pre-Roll-Chance für Live-Streams.

Wenn Ihre Anwendung über eine Chance (Tag) benachrichtigt wird, kann Ihre Anwendung die Timeline ändern, indem sie beispielsweise eine Reihe von Anzeigen einfügt. Standardmäßig ruft Browser TVSDK die entsprechenden auf *`content resolver`* , um die erforderlichen Timeline-Änderungen oder -Aktionen zu implementieren. Ihre Anwendung kann den standardmäßigen Browser TVSDK Advertising Content Resolver verwenden oder einen eigenen Content Resolver registrieren.

Sie können auch `MediaPlayerItemConfig.adTags` , um mehr Anzeigenmarkierungs-Tags/Hinweise für die Standardeinstellung hinzuzufügen `ManifestCuesOpportunityGenerator` -Klasse und -Verwendung `MediaPlayerItemConfig.subscribedTags` damit TVSDK Ihre Anwendung über zusätzliche Tags informieren kann, die möglicherweise über Informationen zum Werbe-Workflow verfügen.

>[!TIP]
>
>Die Standardwerte von `MediaPlayerItemConfig.adTags` und `MediaPlayerItemConfig.subscribeTags` is `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.
