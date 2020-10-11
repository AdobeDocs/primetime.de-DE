---
title: Ad Insertion für VOD verwenden
description: Verwenden von Ad Insertion für VOD
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Ad Insertion für VOD verwenden {#ad-insertion-vod}

Primetime Ad Insertion unterstützt das Einfügen von Anzeigen in mehrere VOD-Assets, wobei die Standardformate VAST 3.0+ oder VMAP 1.0+ verwendet werden.

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD (serverzugeordnete Anzeigen) {#server-mapped-ads}

Primetime-Ad Insertion unterstützt das Einfügen von VOD-Anzeigen, die vor dem Beginn der Wiedergabe eingefügt wurden, unter Verwendung der in einem VMAP-Format definierten Anzeigenzeitschienen.  VMAP-spezifische Anzeigenverfolgung wie breakStart-/breakEnd-Beacons werden mit der [Anzeigenverfolgung](set-up-ad-tracking.md)bereitgestellt.

## Vollständige Wiedergabe von Ereignisse (VOD mit Ad Decisioning-Cues) {#full-event-replay}

Primetime Ad Insertion unterstützt auch spezialisierte VOD-Assets, die Hinweise im Inhaltsstream selbst enthalten, z. B. bei der Wiedergabe bereits aufgezeichneter Live-Ereignis. Weitere Informationen zu den von uns unterstützten Anzeigenentscheidungsformaten (oder Cue-Formaten) finden Sie unter [Verwenden von Ad Insertion in Live/Linear](ad-insertion-live-linear-stream.md).

Wir unterstützen sowohl einzelne Ad-Request- als auch parallele Szenarien mit mehreren Ad-Request-Szenarien für VOD-Assets, die mehr als eine Werbeunterbrechung enthalten. Weitere Informationen finden Sie unter `ptmulticall` Parameter in der [Parameterbeschreibung](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md). Sowohl VAST- als auch VMAP-Formate werden für In-Stream-Hinweise unterstützt.
