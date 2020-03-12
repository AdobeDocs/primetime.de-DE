---
description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-title: VOD-Anzeige auflösen und einfügen
title: VOD-Anzeige auflösen und einfügen
uuid: c1017483-5b4f-4d71-9589-fb2327b4572b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# VOD-Anzeige auflösen und einfügen{#vod-ad-resolving-and-insertion}

Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.

Vor der Wiedergabe löst TVSDK bekannte Anzeigen auf, fügt Anzeigenumbrüche in den Hauptinhalt ein, wie in einer Zeitleiste beschrieben, die von TVSDK zurückgegeben wird, und berechnet die virtuelle Zeitleiste gegebenenfalls neu.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, d. h. vor dem Inhalt.
* **Mid-Roll**, der sich im Inhalt befindet.
* **Post-Roll**, der nach dem Inhalt liegt.

>[!IMPORTANT]
>
>Bei der Implementierung eines benutzerdefinierten `AdPolicySelector`Formulars kann für jeden Typ von `AdBreakTimelineItem` (Pre-Roll, Mid-Roll oder Post-Roll) in eine andere Richtlinie festgelegt werden, `AdPolicyInfo`basierend auf dem Typ des `AdBreakTimelineItem`. Sie können beispielsweise Inhalte mit mittlerem Roll nach der Wiedergabe beibehalten, Inhalte mit Pre-Roll-Charakter jedoch nach der Wiedergabe entfernen.

Nach der Wiedergabe können keine weiteren Beginn am Inhalt auftreten. Anzeigen können nicht sein:

* Eingefügt
* Gelöscht

   So können Sie beispielsweise keine integrierten Anzeigen aus den Inhalten löschen, um ein werbefreies Erlebnis Angebot.
* Ersetzt

   Beispielsweise können integrierte Anzeigen nicht durch zielgerichtete Anzeigen ersetzt werden.

