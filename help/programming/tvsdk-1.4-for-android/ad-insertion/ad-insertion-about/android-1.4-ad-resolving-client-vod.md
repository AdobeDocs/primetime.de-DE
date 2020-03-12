---
description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-title: VOD-Anzeige auflösen und einfügen
title: VOD-Anzeige auflösen und einfügen
uuid: 33280792-ad08-41c1-b180-cc2159e8137c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# VOD-Anzeige auflösen und einfügen{#vod-ad-resolving-and-insertion}

Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.

Vor der Wiedergabe löst TVSDK bekannte Anzeigen, fügt Anzeigenumbrüche in den Hauptinhalt ein, wie in einer Zeitleiste beschrieben, die von Adobe Primetime-Anzeigenentscheidung zurückgegeben wird, und berechnet die virtuelle Zeitschiene ggf. neu.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, d. h. vor dem Inhalt.
* **Mid-Roll**, der sich im Inhalt befindet.
* **Post-Roll**, der nach dem Inhalt liegt.

Nach der Wiedergabe können keine weiteren Beginn am Inhalt auftreten. Anzeigen können nicht sein:

* Eingefügt
* Gelöscht

   So können Sie beispielsweise keine integrierten Anzeigen aus den Inhalten löschen, um ein werbefreies Erlebnis Angebot.
* Ersetzt

   Beispielsweise können integrierte Anzeigen nicht durch zielgerichtete Anzeigen ersetzt werden.

