---
description: Bei Live-/linearen Inhalten ersetzt Browser TVSDK einen Teil des Hauptstream-Inhalts durch eine Werbeunterbrechung derselben Dauer, sodass die Timeline-Dauer unverändert bleibt.
title: Auflösung und Einfügen von Live/linearen Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Auflösung und Einfügen von Live/linearen Anzeigen{#live-linear-ad-resolving-and-insertion}

Bei Live-/linearen Inhalten ersetzt Browser TVSDK einen Teil des Hauptstream-Inhalts durch eine Werbeunterbrechung derselben Dauer, sodass die Timeline-Dauer unverändert bleibt.

Vor und während der Wiedergabe löst Browser TVSDK bekannte Anzeigen auf, ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen derselben Dauer und berechnet bei Bedarf die virtuelle Timeline neu. Die Positionen der Werbeunterbrechungen werden durch Cue-Punkte festgelegt, die durch das Manifest definiert werden.

Browser TVSDK fügt Anzeigen wie folgt ein:

* **Pre-roll**, der sich am Anfang des Inhalts befindet.

Browser TVSDK akzeptiert die Werbeunterbrechung, selbst wenn die Dauer der Cue-Punkt-Ersetzung länger oder kürzer ist. Browser TVSDK unterstützt standardmäßig die `#EXT-X-CUE` Cue-Point als gültige Anzeigenmarke beim Auflösen und Platzieren von Anzeigen. Diese Markierung erfordert das Metadatenfeld `DURATION` in Sekunden und der eindeutigen Kennung des Cue-Point. Beispiel:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Sie können zusätzliche Hinweise (Tags) definieren und abonnieren.

Nach dem Start der Wiedergabe aktualisiert das Video-Engine die Manifestdatei regelmäßig. Browser TVSDK löst alle neuen Anzeigen auf und fügt die Anzeigen ein, wenn ein Cue-Punkt im Live- oder linearen Stream auftritt, der im Manifest definiert wurde. Nachdem Anzeigen aufgelöst und eingefügt wurden, berechnet Browser TVSDK die virtuelle Timeline erneut und sendet eine `AdobePSDK.PSDKEventType.TIMELINE_UPDATED` -Ereignis.

>[!TIP]
>
>Bei Live-Streams unterstützt Browser TVSDK nur MP4- und HLS-Pre-Roll- und Mid-Roll-Anzeigen.
