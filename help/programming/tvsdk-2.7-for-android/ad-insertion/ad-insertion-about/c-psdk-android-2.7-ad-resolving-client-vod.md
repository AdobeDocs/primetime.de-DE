---
description: Bei Video-On-Demand (VOD)-Inhalten fügt TVSDK die Anzeigen durch Aufspaltung der Anzeigen im Hauptinhalt ein, sodass die Timeline-Dauer erhöht wird.
title: Auflösen und Einfügen von VOD-Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Auflösen und Einfügen von VOD-Anzeigen {#resolve-and-insert-vod-ad}

Bei Video-On-Demand (VOD)-Inhalten fügt TVSDK die Anzeigen durch Aufspaltung der Anzeigen im Hauptinhalt ein, sodass die Timeline-Dauer erhöht wird.

TVSDK löst vor der Wiedergabe bekannte Anzeigen auf, fügt Anzeigen ein und unterbricht sie im Hauptinhalt, wie durch eine Timeline beschrieben, die von der Adobe Primetime-Anzeigenentscheidung zurückgegeben wird, und berechnet die virtuelle Timeline ggf. neu.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-roll**, der vor dem Inhalt platziert wird.
* **Mid-roll**, der sich in der Mitte des Inhalts befindet.
* **Post-Roll**, der hinter dem Inhalt platziert wird.

>[!TIP]
>
>Nach dem Start der Wiedergabe können keine weiteren Änderungen am Inhalt vorgenommen werden.

Anzeigen können nicht sein:

* Einfügen
* Gelöscht

  Sie können beispielsweise keine integrierten Anzeigen aus dem Inhalt löschen, um ein anzeigenfreies Erlebnis anzubieten.
* Ersetzt

  Sie können beispielsweise keine integrierten Anzeigen durch zielgerichtete Anzeigen ersetzen.
