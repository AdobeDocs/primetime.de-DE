---
description: Bei Live-/linearen Inhalten ersetzt Browser TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung gleicher Dauer, sodass die Zeitschiene unverändert bleibt.
title: Live/Lineare Anzeigenauflösung und -einfügung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Auflösung und Einfügen von Live-/Linearen Anzeigen{#live-linear-ad-resolving-and-insertion}

Bei Live-/linearen Inhalten ersetzt Browser TVSDK einen Abschnitt des Hauptstream-Inhalts durch eine Werbeunterbrechung gleicher Dauer, sodass die Zeitschiene unverändert bleibt.

Vor und während der Wiedergabe löst Browser TVSDK bekannte Anzeigen, ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen gleicher Dauer und berechnet bei Bedarf die virtuelle Zeitschiene neu. Die Positionen der Werbeunterbrechungen werden durch Cue-Points festgelegt, die durch das Manifest definiert werden.

Browser TVSDK fügt Anzeigen wie folgt ein:

* **Pre-Roll**, der sich am Anfang des Inhalts befindet.

Browser TVSDK akzeptiert die Werbeunterbrechung, selbst wenn die Dauer länger oder kürzer als die Dauer des Cue-Point-Austauschs ist. Browser TVSDK unterstützt standardmäßig das `#EXT-X-CUE`-Cue als gültige Anzeigenmarke beim Auflösen und Platzieren von Anzeigen. Für diese Markierung ist das Metadatenfeld `DURATION` in Sekunden und die eindeutige ID des Cue erforderlich. Beispiel:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Sie können zusätzliche Hinweise (Tags) definieren und abonnieren.

Nach Beginn der Wiedergabe aktualisiert die Video-Engine die Manifestdatei in regelmäßigen Abständen. Browser TVSDK löst alle neuen Anzeigen und fügt die Anzeigen ein, wenn ein Cue-Point im Live- oder linearen Stream gefunden wird, der im Manifest definiert wurde. Nachdem Anzeigen aufgelöst und eingefügt wurden, berechnet Browser TVSDK die virtuelle Zeitleiste erneut und löst ein `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`-Ereignis aus.

>[!TIP]
>
>Für Live-Streams unterstützt Browser TVSDK nur MP4- und HLS-Pre-Roll- und Mid-Roll-Anzeigen.

