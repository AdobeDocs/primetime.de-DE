---
description: Bei VOD-Inhalten (Video-on-Demand) fügt Browser TVSDK Werbeunterbrechungen ein, indem die Anzeigen im Hauptinhalt geteilt werden, sodass die Zeitschiene länger ist.
title: VOD-Anzeige auflösen und einfügen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
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

