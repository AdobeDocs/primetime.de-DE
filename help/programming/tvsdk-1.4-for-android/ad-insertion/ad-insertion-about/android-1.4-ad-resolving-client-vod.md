---
description: Bei Video-On-Demand (VOD)-Inhalten fügt TVSDK die Anzeigen durch Aufspaltung der Anzeigen im Hauptinhalt ein, sodass die Timeline-Dauer erhöht wird.
title: Auflösung und Einfügen von VOD-Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# Auflösung und Einfügen von VOD-Anzeigen{#vod-ad-resolving-and-insertion}

Bei Video-On-Demand (VOD)-Inhalten fügt TVSDK die Anzeigen durch Aufspaltung der Anzeigen im Hauptinhalt ein, sodass die Timeline-Dauer erhöht wird.

TVSDK löst vor der Wiedergabe bekannte Anzeigen auf, fügt Anzeigen ein und unterbricht sie im Hauptinhalt, wie durch eine Timeline beschrieben, die von der Adobe Primetime-Anzeigenentscheidung zurückgegeben wird, und berechnet die virtuelle Timeline ggf. neu.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-roll**, der vor dem Inhalt steht.
* **Mid-roll**, der sich im Inhalt befindet.
* **Post-Roll**, der hinter dem Inhalt steht.

Nach dem Start der Wiedergabe können keine weiteren Änderungen am Inhalt vorgenommen werden. Anzeigen können nicht sein:

* Einfügen
* Gelöscht

  Sie können beispielsweise keine integrierten Anzeigen aus dem Inhalt löschen, um ein anzeigenfreies Erlebnis anzubieten.
* Ersetzt

  Sie können beispielsweise keine integrierten Anzeigen durch zielgerichtete Anzeigen ersetzen.
