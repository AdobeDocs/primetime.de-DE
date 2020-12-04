---
description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.
seo-description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.
seo-title: Live/Lineare Anzeigenauflösung und -einfügung
title: Live/Lineare Anzeigenauflösung und -einfügung
uuid: a63c97c3-00c5-4dee-a42c-30b70e432b93
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Auflösung und Einfügen von Live-/Linearen Anzeigen {#live-linear-ad-resolving-and-insertion}

Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.

Vor und während der Wiedergabe löst TVSDK bekannte Anzeigen, ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen gleicher Dauer und berechnet bei Bedarf die virtuelle Zeitschiene neu. Die Positionen der Werbeunterbrechungen werden durch Cue-Points festgelegt, die vom Manifest definiert werden.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, am Anfang des Inhalts.
* **Mid-Roll** in der Mitte des Inhalts.

TVSDK akzeptiert die Werbeunterbrechung, selbst wenn die Dauer länger oder kürzer als die Cue-Point-Ersetzungsdauer ist. TVSDK unterstützt standardmäßig das `#EXT-X-CUE`-Cue als gültige Anzeigenmarke beim Auflösen und Platzieren von Anzeigen. Für diese Markierung ist das Metadatenfeld `DURATION` in Sekunden und die eindeutige ID des Cue erforderlich. Beispiel:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Sie können zusätzliche Hinweise (Tags) definieren und abonnieren.

Nach Beginn der Wiedergabe aktualisiert die Video-Engine die Manifestdatei in regelmäßigen Abständen. TVSDK löst alle neuen Anzeigen und fügt die Anzeigen ein, wenn ein Cue-Point im Live- oder linearen Stream gefunden wird, der im Manifest definiert wurde. Nachdem Anzeigen aufgelöst und eingefügt wurden, berechnet TVSDK die virtuelle Zeitleiste erneut und löst ein `TimelineItemsUpdatedEventListener.onTimelineUpdated`-Ereignis aus.
