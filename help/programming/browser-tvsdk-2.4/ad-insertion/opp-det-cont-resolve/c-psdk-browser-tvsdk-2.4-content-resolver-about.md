---
description: Browser TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest angegebenen Möglichkeiten ändern.
seo-description: Browser TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest angegebenen Möglichkeiten ändern.
seo-title: Opportunity-Generatoren und Content-Auflösungen
title: Opportunity-Generatoren und Content-Auflösungen
uuid: e462ad89-1609-4efa-aa67-cfd04f045927
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Opportunity-Generatoren und Content-Auflösungen{#opportunity-generators-and-content-resolvers}

Browser TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest angegebenen Möglichkeiten ändern.

Ein *`opportunity`* Punkt, der auf der Zeitschiene interessant ist und normalerweise auf eine Werbeplatzierungsmöglichkeit hinweist. Diese Gelegenheit kann auch einen benutzerdefinierten Vorgang anzeigen, der sich auf die Zeitschiene auswirken könnte. Ein *`opportunity generator`* identifiziert bestimmte Möglichkeiten (Tags) in der Zeitschiene und benachrichtigt TVSDK, dass diese Möglichkeiten getaggt wurden.

Chancen werden in einem Zeitplan in `TimedMetata`aufgeführt. Die Funktion `ManifestCuesOpportunityGenerator` bietet Möglichkeiten basierend auf den `TimedMetadata` Objekten, die für jedes Splice-out-Anzeigen-Tag (in) erstellt wurden, das im Manifest erkannt wurde `MediaPlayerItemConfig.adTags`. Die `AdSignalingModeOpportunityGenerator` Funktion bietet die anfängliche Möglichkeit, die auf dem `MediaPlayerItem` Typ und dem zugehörigen Anzeigensignalisierungsmodus basiert.

>[!TIP]
>
>Wenn die `AdvertisingMetadata.livePreroll` oder die `AdvertisingMetadata.preroll` -Eigenschaft festgelegt ist, `AdSignalingModeOpportunityGenerator` wird eine Pre-Roll-Gelegenheit für Live-Streams generiert.

Wenn Ihre Anwendung über eine Gelegenheit (Tag) benachrichtigt wird, kann Ihre Anwendung die Zeitschiene ändern, indem Sie beispielsweise eine Reihe von Anzeigen einfügen. Standardmäßig ruft Browser TVSDK die passenden auf, *`content resolver`* um die erforderlichen Änderungen oder Aktionen in der Zeitleiste zu implementieren. Ihre Anwendung kann den standardmäßigen Browser TVSDK Advertisement Content-Auflöser verwenden oder einen eigenen Content-Auflöser registrieren.

Sie können auch mehr Anzeigenmarken-Tags/Hinweise für die Standard- `MediaPlayerItemConfig.adTags` Klasse hinzufügen und verwenden, `ManifestCuesOpportunityGenerator` `MediaPlayerItemConfig.subscribedTags` damit TVSDK Ihre Anwendung über zusätzliche Tags benachrichtigen kann, die möglicherweise Informationen zum Anzeigen-Workflow enthalten.

>[!TIP]
>
>Die Standardwerte von `MediaPlayerItemConfig.adTags` und `MediaPlayerItemConfig.subscribeTags` sind `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.

