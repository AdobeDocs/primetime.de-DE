---
description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-title: VOD-Anzeige auflösen und einfügen
title: VOD-Anzeige auflösen und einfügen
uuid: 69853c16-e252-472e-b33a-7a0e0c4b95dd
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Auflösen und Einfügen von VOD-Anzeigen {#resolve-and-insert-vod-ad}

Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.

Vor der Wiedergabe löst TVSDK bekannte Anzeigen auf, fügt Anzeigenumbrüche in den Hauptinhalt ein, wie in einer Zeitleiste beschrieben, die von der Adobe Primetime-Anzeigenentscheidung zurückgegeben wird, und berechnet bei Bedarf die virtuelle Zeitschiene neu.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, der vor dem Inhalt platziert wird.
* **Mid-Roll**, der sich in der Mitte des Inhalts befindet.
* **Post-Roll**, der nach dem Inhalt platziert wird.

>[!TIP]
>
>Nach der Wiedergabe können keine weiteren Beginn am Inhalt auftreten.

Anzeigen können nicht sein:

* Eingefügt
* Gelöscht

   So können Sie beispielsweise keine integrierten Anzeigen aus den Inhalten löschen, um ein werbefreies Erlebnis Angebot.
* Ersetzt

   Beispielsweise können integrierte Anzeigen nicht durch zielgerichtete Anzeigen ersetzt werden.

