---
title: Ad Insertion für VOD verwenden
description: Verwenden von Ad Insertion für VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Ad Insertion für VOD verwenden {#ad-insertion-vod}

Primetime Ad Insertion unterstützt das Einfügen von Anzeigen in mehrere VOD-Assets, wobei die standardmäßigen Formate VAST 3.0+ oder VMAP 1.0+ verwendet werden.

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD (Anzeigenzuordnungen) {#server-mapped-ads}

Primetime Ad Insertion unterstützt das Einfügen von VOD-Anzeigen mit Anzeigen, die vor dem Anfang der Wiedergabe eingefügt wurden, und verwendet dabei die in einem VMAP-Format definierten Anzeigenzeitlinien.  VMAP-spezifisches Anzeigen-Tracking wie breakStart/breakEnd-Beacons wird mit [Anzeigen-Tracking](set-up-ad-tracking.md).

## Vollständige Ereigniswiedergabe (VOD mit Ad Decisioning-Cues) {#full-event-replay}

Primetime Ad Insertion unterstützt auch spezialisierte VOD-Assets, die Hinweise im Inhalts-Stream selbst enthalten, z. B. bei der Wiedergabe von zuvor aufgezeichneten Live-Ereignissen. Weitere Informationen zu den von uns unterstützten Arten von Ad Decisioning-Hinweisen (oder Cue-Formaten) finden Sie unter [Verwenden von Ad Insertion in Live/Linear](ad-insertion-live-linear-stream.md).

Wir unterstützen sowohl Einzelne Anzeigenanfragen als auch parallele Szenarien mit mehreren Anzeigenanfragen für VOD-Assets, die mehr als eine Werbeunterbrechung enthalten. Weitere Informationen finden Sie unter `ptmulticall` Parameter in [Parameterbeschreibung](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md). Für In-Stream-Hinweise werden sowohl VAST- als auch VMAP-Formate unterstützt.
