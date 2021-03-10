---
description: Für Video-on-Demand-Inhalte (VOD) fügt TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt aufgeteilt werden, sodass die Zeitschiene länger ist.
title: VOD-Anzeige auflösen und einfügen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
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