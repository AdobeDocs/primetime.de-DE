---
description: Bei VOD-Inhalten (Video-on-Demand) fügt Browser TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt geteilt werden, sodass die Zeitschiene länger ist.
seo-description: Bei VOD-Inhalten (Video-on-Demand) fügt Browser TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt geteilt werden, sodass die Zeitschiene länger ist.
seo-title: VOD-Anzeige auflösen und einfügen
title: VOD-Anzeige auflösen und einfügen
uuid: 34a30ae5-d553-4c5d-9829-8e5eaa41c104
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# VOD-Anzeige auflösen und einfügen{#vod-ad-resolving-and-insertion}

Bei VOD-Inhalten (Video-on-Demand) fügt Browser TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt geteilt werden, sodass die Zeitschiene länger ist.

Vor der Wiedergabe löst Browser TVSDK bekannte Anzeigen auf, fügt Anzeigenumbrüche in den Hauptinhalt ein, wie in einer Zeitleiste beschrieben, die von Adobe Primetime bei der Anzeigenentscheidung zurückgegeben wird, und berechnet die virtuelle Zeitschiene ggf. neu.

Browser TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, d. h. vor dem Inhalt.
* **Post-Roll**, der nach dem Inhalt liegt.

Nach der Wiedergabe können keine weiteren Beginn am Inhalt auftreten. Anzeigen können nicht sein:

* Eingefügt
* Gelöscht

   So können Sie beispielsweise keine integrierten Anzeigen aus den Inhalten löschen, um ein werbefreies Erlebnis Angebot.
* Ersetzt

   Beispielsweise können integrierte Anzeigen nicht durch zielgerichtete Anzeigen ersetzt werden.

