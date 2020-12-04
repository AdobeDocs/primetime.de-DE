---
description: Browser TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest angegebenen Möglichkeiten ändern.
seo-description: Browser TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest angegebenen Möglichkeiten ändern.
seo-title: Opportunity-Generatoren und Content-Auflösungen
title: Opportunity-Generatoren und Content-Auflösungen
uuid: e462ad89-1609-4efa-aa67-cfd04f045927
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Opportunity-Generatoren und Content-Auflöser{#opportunity-generators-and-content-resolvers}

Browser TVSDK bietet standardmäßige Opportunitätserzeuger und Content-Auflöser, die Anzeigen in der Zeitleiste platzieren. Diese Generatoren und Auflösungen basieren auf nicht standardmäßigen Tags im Manifest. Möglicherweise muss Ihre Anwendung die Zeitschiene entsprechend den im Manifest angegebenen Möglichkeiten ändern.

Ein *`opportunity`* stellt einen Interessensort auf der Zeitschiene dar, der normalerweise auf eine Anzeigenplatzierungsmöglichkeit hinweist. Diese Gelegenheit kann auch einen benutzerdefinierten Vorgang anzeigen, der sich auf die Zeitschiene auswirken könnte. Ein *`opportunity generator`* identifiziert bestimmte Möglichkeiten (Tags) in der Zeitleiste und benachrichtigt TVSDK, dass diese Möglichkeiten getaggt wurden.

Chancen werden in einer Zeitschiene in `TimedMetata` identifiziert. Das `ManifestCuesOpportunityGenerator` erstellt Chancen auf Grundlage der `TimedMetadata`-Objekte, die für jedes Splice-out-Anzeigen-Tag (in `MediaPlayerItemConfig.adTags`) erstellt wurden, das im Manifest erkannt wurde. Das `AdSignalingModeOpportunityGenerator` erstellt die anfängliche Chance, die auf dem `MediaPlayerItem`-Typ und dem zugehörigen Anzeigensignalisierungsmodus basiert.

>[!TIP]
>
>Wenn die Eigenschaft `AdvertisingMetadata.livePreroll` oder `AdvertisingMetadata.preroll` festgelegt ist, generiert `AdSignalingModeOpportunityGenerator` eine Pre-Roll-Gelegenheit für Live-Streams.

Wenn Ihre Anwendung über eine Gelegenheit (Tag) benachrichtigt wird, kann Ihre Anwendung die Zeitschiene ändern, indem Sie beispielsweise eine Reihe von Anzeigen einfügen. Browser TVSDK ruft standardmäßig das entsprechende *`content resolver`* auf, um die erforderlichen Änderungen oder Aktionen der Zeitschiene zu implementieren. Ihre Anwendung kann den standardmäßigen Browser TVSDK Advertisement Content-Auflöser verwenden oder einen eigenen Content-Auflöser registrieren.

Sie können `MediaPlayerItemConfig.adTags` auch verwenden, um mehr Anzeigenmarken-Tags/Hinweise für die standardmäßige `ManifestCuesOpportunityGenerator`-Klasse hinzuzufügen und `MediaPlayerItemConfig.subscribedTags` zu verwenden, damit TVSDK Ihre Anwendung über zusätzliche Tags benachrichtigen kann, die möglicherweise Informationen zum Werbe-Workflow enthalten.

>[!TIP]
>
>Die Standardwerte von `MediaPlayerItemConfig.adTags` und `MediaPlayerItemConfig.subscribeTags` sind `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.

