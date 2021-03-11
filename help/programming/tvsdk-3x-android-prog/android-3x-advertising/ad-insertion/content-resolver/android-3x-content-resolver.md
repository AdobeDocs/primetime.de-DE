---
description: Ein Opportunitätsgenerator identifiziert Platzierungsmöglichkeiten durch benutzerdefinierte Tags in einem Stream, benutzerdefinierte Anzeigensignalisierungsmodi usw. Der Opportunitätsgenerator sendet diese Platzierungsmöglichkeiten an den Content-Auflöser, der den Arbeitsablauf zum Einfügen von Inhalten/Anzeigen basierend auf den Eigenschaften und Metadaten der Platzierungsmöglichkeit anpasst.
title: Anpassen von Opportunitätserzeugern und Inhaltsauflösungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '207'
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

* Erkennen Sie benutzerdefinierte Tags für das Einfügen von Anzeigen. Weitere Informationen finden Sie unter [Gelegenheitsgeneratoren und Inhaltsauflöser anpassen](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/content-resolver/android-3x-content-resolver.md).
* Erstellen Sie einen benutzerdefinierten Anzeigenanbieter.
* Inhalt schwarz ausblenden.