---
description: Der Manifestserver unterstützt für alle HLS-Videoformate WebVTT-Untertitel, die vom Herausgeber aktiviert wurden. Wenn sie Anforderungen zum Einfügen von Anzeigen in mit WebVTT unterschriebene Inhalte erhält, erfolgt dies korrekt.
seo-description: Der Manifestserver unterstützt für alle HLS/DASH-Videoformate WebVTT-Untertitel, die vom Herausgeber aktiviert wurden. Wenn sie Anforderungen zum Einfügen von Anzeigen in mit WebVTT unterschriebene Inhalte erhält, erfolgt dies korrekt.
seo-title: Unterstützung für WebVTT-Beschriftungen
title: Unterstützung für WebVTT-Beschriftungen
uuid: 1dc728b0-5aeb-4c48-8f3b-54ff4b135742
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# Unterstützung für WebVTT-Beschriftungen {#support-for-webvtt-captions}

Der Manifestserver unterstützt für Herausgeber aktivierte WebVTT-Beschriftungen für HLS/DASH-Videoformate. Wenn sie Anforderungen zum Einfügen von Anzeigen in mit WebVTT unterschriebene Inhalte erhält, erfolgt dies korrekt.

Wenn der Herausgeber WebVTT-Untertitel im Inhalt enthält, sendet der Manifestserver dem Client einen Inhaltsstream mit Untertiteln. WebVTT muss vom Herausgeber aktiviert werden, damit der Manifestserver Untertitel unterstützen kann. Wenn der Client WebVTT-Untertitel aktiviert hat und eine Anforderung an den Manifestserver sendet, manipuliert der Manifestserver die Zeitschiene und WebVTT-Verfolgung und gibt Inhalte mit zugefügten Anzeigen und Untertiteln an den Client zurück.

Der Arbeitsablauf für VOD-Inhaltsströme lautet wie folgt:

1. Der Client sendet einen Inhaltsstream mit aktivierten WebVTT-Untertiteln an den Manifestserver.
1. Der Manifestserver manipuliert die Zeitschiene, um Anzeigen in den Inhaltsstream zu binden.
1. Der Manifestserver manipuliert die WebVTT-Verfolgung, um dem Inhalt Untertitel hinzuzufügen (einschließlich Anzeigen).
1. Der Manifestserver liefert den Inhaltsstream mit eingefügten Anzeigen und Beschriftungen an den Client.

>[!NOTE]
>
>Wenn ein WebVTT-Beschriftungssegment in eine Mid-Roll-Anzeige fällt, sieht der Viewer die Beschriftung vor und nach dieser Mid-Roll-Werbeunterbrechung. In einem 10-Sekunden-Beschriftungssegment mit einer 30-Sekunden-Mid-Roll-Anzeige bei 5-Sekunden-Markierung sieht der Viewer dieses Beschriftungssegment beispielsweise 5 Sekunden vor der Mid-Roll-Werbeunterbrechung und 5 Sekunden nach der Mid-Roll-Unterbrechung.

>[!NOTE]
>
>Wenn ein Client anfordert, dass ein Video in einer bestimmten Sprache wie Englisch abgespielt wird, und dann die Wiedergabe des Videos auf Französisch anfordert, kann der Manifestserver nicht erkennen, dass der Client die Sprache in Französisch ändern muss. Da der Client nicht mit dem Manifestserver kommuniziert, fügt der Manifestserver die Anzeigenbeschriftung in den Videostream ein, wobei die erste in der Anzeigendatei &quot;M3U8 Übergeordnet&quot;angegebene Sprache verwendet wird.
