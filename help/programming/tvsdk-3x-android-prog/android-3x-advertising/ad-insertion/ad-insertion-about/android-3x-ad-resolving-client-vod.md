---
description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
seo-title: VOD-Anzeige auflösen und einfügen
title: VOD-Anzeige auflösen und einfügen
uuid: b7124cab-441b-4b38-ac83-300ab9e5f9ec
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Auflösen und Einfügen von VOD-Anzeigen {#resolve-and-insert-vod-ad}

Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.

Vor der Wiedergabe löst TVSDK bekannte Anzeigen, fügt Anzeigenumbrüche in den Hauptinhalt ein, wie in einer Zeitleiste beschrieben, die von Adobe Primetime-Anzeigenentscheidung zurückgegeben wird, und berechnet die virtuelle Zeitschiene ggf. neu.

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