---
description: Bei Live-/linearen Inhalten ersetzt TVSDK einen Teil des Hauptstream-Inhalts durch eine Werbeunterbrechung derselben Dauer, sodass die Timeline-Dauer unverändert bleibt.
title: Auflösung und Einfügen von Live/linearen Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Auflösung und Einfügen von Live/linearen Anzeigen {#live-linear-ad-resolving-and-insertion}

Bei Live-/linearen Inhalten ersetzt TVSDK einen Teil des Hauptstream-Inhalts durch eine Werbeunterbrechung derselben Dauer, sodass die Timeline-Dauer unverändert bleibt.

TVSDK löst vor und während der Wiedergabe bekannte Anzeigen auf, ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen derselben Dauer und berechnet bei Bedarf die virtuelle Timeline neu. Die Positionen der Werbeunterbrechungen werden durch Cue-Punkte festgelegt, die durch das Manifest definiert werden.

TVSDK fügt Anzeigen wie folgt ein:

* **Pre-roll**, am Anfang des Inhalts.
* **Mid-roll**, in der Mitte des Inhalts.

TVSDK akzeptiert die Werbeunterbrechung auch dann, wenn die Dauer länger oder kürzer als die Cue-Point-Ersetzungsdauer ist. TVSDK unterstützt standardmäßig die `#EXT-X-CUE` Cue-Point als gültige Anzeigenmarke beim Auflösen und Platzieren von Anzeigen. Diese Markierung erfordert das Metadatenfeld `DURATION` in Sekunden und der eindeutigen Kennung des Cue-Point. Beispiel:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

Sie können zusätzliche Hinweise (Tags) definieren und abonnieren.

Nach dem Start der Wiedergabe aktualisiert das Video-Engine die Manifestdatei regelmäßig. TVSDK löst alle neuen Anzeigen auf und fügt die Anzeigen ein, wenn ein Cue-Punkt im im Manifest definierten Live- oder linearen Stream auftritt. Nachdem Anzeigen aufgelöst und eingefügt wurden, berechnet TVSDK die virtuelle Timeline erneut und sendet eine `TimelineItemsUpdatedEventListener.onTimelineUpdated` -Ereignis.
