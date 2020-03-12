---
description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.
seo-description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.
seo-title: Auflösen und Einfügen einer Live-/linearen Anzeige
title: Auflösen und Einfügen einer Live-/linearen Anzeige
uuid: c9d54fc9-1d54-41c3-a872-d27afdd16314
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Auflösen und Einfügen von Live-/linearen Anzeigen {#resolve-and-insert-live-linear-ad}

Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.

Vor und während der Wiedergabe löst TVSDK bekannte Anzeigen, ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen gleicher Dauer und berechnet bei Bedarf die virtuelle Zeitschiene neu. Die Positionen der Werbeunterbrechungen werden durch Cue-Points festgelegt, die durch das Manifest definiert werden.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, der vor dem Inhalt platziert wird.
* **Mid-Roll**, der in der Mitte des Inhalts platziert wird.

TVSDK akzeptiert die Werbeunterbrechung, selbst wenn die Dauer länger oder kürzer als die Cue-Point-Ersetzungsdauer ist. TVSDK unterstützt den `#EXT-X-CUE` Cue-Point standardmäßig als gültige Anzeigenmarke beim Auflösen und Platzieren von Anzeigen. Für diese Markierung müssen der Metadatenfeldwert in Sekunden und die eindeutige ID des Cue- `DURATION` Cue-Points angegeben werden. Beispiel:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Sie können zusätzliche Hinweise (Tags) definieren und abonnieren.

Nach Beginn der Wiedergabe aktualisiert die Video-Engine die Manifestdatei in regelmäßigen Abständen. TVSDK löst alle neuen Anzeigen und fügt die Anzeigen ein, wenn ein Cue-Point im Live- oder linearen Stream gefunden wird, der im Manifest definiert wurde. Nachdem Anzeigen aufgelöst und eingefügt wurden, berechnet TVSDK die virtuelle Zeitleiste erneut und löst ein `TimelineItemsUpdatedEventListener.onTimelineUpdated` Ereignis aus.
