---
description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
title: VOD-Anzeige auflösen und einfügen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

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
>Bei der Implementierung eines benutzerdefinierten `AdPolicySelector` kann jeder Typ von `AdBreakTimelineItem` (Pre-Roll, Mid-Roll oder Post-Roll) in `AdPolicyInfo` je nach Typ des `AdBreakTimelineItem` eine andere Richtlinie zugewiesen werden. Sie können beispielsweise Inhalte mit mittlerem Roll nach der Wiedergabe beibehalten, Inhalte mit Pre-Roll-Charakter jedoch nach der Wiedergabe entfernen.

Nach der Wiedergabe können keine weiteren Beginn am Inhalt auftreten. Anzeigen können nicht sein:

* Eingefügt
* Gelöscht

   So können Sie beispielsweise keine integrierten Anzeigen aus den Inhalten löschen, um ein werbefreies Erlebnis Angebot.
* Ersetzt

   Beispielsweise können integrierte Anzeigen nicht durch zielgerichtete Anzeigen ersetzt werden.

