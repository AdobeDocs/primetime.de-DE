---
description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.
seo-description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.
seo-title: Live/Lineare Anzeigenauflösung und -einfügung
title: Live/Lineare Anzeigenauflösung und -einfügung
uuid: 69f287aa-b707-442b-8e07-16f81b242c4b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Auflösung und Einfügen von Live-/Linearen Anzeigen{#live-linear-ad-resolving-and-insertion}

Bei Live-/linearen Inhalten ersetzt TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung mit der gleichen Dauer, sodass die Zeitschienendauer unverändert bleibt.

Vor und während der Wiedergabe löst TVSDK bekannte Anzeigen, ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen gleicher Dauer und berechnet bei Bedarf die virtuelle Zeitschiene neu. Die Positionen der Werbeunterbrechungen werden durch Cue-Points festgelegt, die durch das Manifest definiert werden.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, der sich am Anfang des Inhalts befindet.
* **Mid-Roll**, der sich in der Mitte des Inhalts befindet.

TVSDK akzeptiert die Werbeunterbrechung, selbst wenn die Dauer länger oder kürzer als die Cue-Point-Ersetzungsdauer ist. TVSDK unterstützt standardmäßig das `#EXT-X-CUE`-Cue als gültige Anzeigenmarke beim Auflösen und Platzieren von Anzeigen. Für diese Markierung ist das Metadatenfeld `DURATION` in Sekunden und die eindeutige ID des Cue erforderlich. Beispiel:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

>[!IMPORTANT]
>
>Bei der Implementierung eines herkömmlichen `AdPolicySelector` kann eine andere Richtlinie für Pre-Roll-, Mid-Roll- und Post-Roll `AdBreakTimelineItem`s in `AdPolicyInfo` angegeben werden, die auf dem Typ der `AdBreakTimelineItem`s basiert. Sie können beispielsweise Inhalte mit mittlerem Roll nach der Wiedergabe beibehalten, Inhalte mit Pre-Roll-Unterbrechung nach der Wiedergabe jedoch entfernen.

Nach Beginn der Wiedergabe aktualisiert die Video-Engine die Manifestdatei in regelmäßigen Abständen. TVSDK löst alle neuen Anzeigen und fügt die Anzeigen ein, wenn ein Cue-Point im Live- oder linearen Stream gefunden wird, der im Manifest definiert wurde. Nachdem Anzeigen aufgelöst und eingefügt wurden, berechnet TVSDK die virtuelle Zeitleiste erneut und löst ein `TimelineEvent.TIMELINE_UPDATED`-Ereignis aus.
