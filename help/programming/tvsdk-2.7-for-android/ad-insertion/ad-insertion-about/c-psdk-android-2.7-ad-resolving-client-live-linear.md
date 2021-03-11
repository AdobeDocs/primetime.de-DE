---
description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.
title: Auflösen und Einfügen einer Live-/linearen Anzeige
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Auflösen und Einfügen von Live-/linearen Anzeigen {#resolve-and-insert-live-linear-ad}

Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.

Vor und während der Wiedergabe löst TVSDK bekannte Anzeigen, ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen gleicher Dauer und berechnet bei Bedarf die virtuelle Zeitschiene neu. Die Positionen der Werbeunterbrechungen werden durch Cue-Points festgelegt, die durch das Manifest definiert werden.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, der vor dem Inhalt platziert wird.
* **Mid-Roll**, der in der Mitte des Inhalts platziert wird.

TVSDK akzeptiert die Werbeunterbrechung, selbst wenn die Dauer länger oder kürzer als die Cue-Point-Ersetzungsdauer ist. TVSDK unterstützt standardmäßig das `#EXT-X-CUE`-Cue als gültige Anzeigenmarke beim Auflösen und Platzieren von Anzeigen. Für diese Markierung müssen das Metadatenfeld `DURATION` in Sekunden und die eindeutige ID des Cue-Points angegeben werden. Beispiel:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Sie können zusätzliche Hinweise (Tags) definieren und abonnieren.

Nach Beginn der Wiedergabe aktualisiert die Video-Engine die Manifestdatei in regelmäßigen Abständen. TVSDK löst alle neuen Anzeigen und fügt die Anzeigen ein, wenn ein Cue-Point im Live- oder linearen Stream gefunden wird, der im Manifest definiert wurde. Nachdem Anzeigen aufgelöst und eingefügt wurden, berechnet TVSDK die virtuelle Zeitleiste erneut und löst ein `TimelineItemsUpdatedEventListener.onTimelineUpdated`-Ereignis aus.
