---
description: Sie können Zeitschienen für Werbeunterbrechungen in VOD-Inhalten mit einer formatierten Liste von Anzeigen- und Inhaltssegmenten, so genannten Pods, angeben oder überschreiben.
title: VOD-Timeline-Format
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# VOD-Timeline-Format {#vod-timeline-format}

Sie können Zeitschienen für Werbeunterbrechungen in VOD-Inhalten mit einer formatierten Liste von Anzeigen- und Inhaltssegmenten, so genannten Pods, angeben oder überschreiben.

## Pods {#section_606E9456E25E41C8B8537A023DDD96CE}

Ein Pod ist eine Werbeunterbrechung oder ein Inhaltssegment. Eine Zeitleiste besteht aus einer durch Semikolons getrennten Sequenz von Pods. Die folgenden Pods sind vorhanden:

### Werbeunterbrechung

```
B,duration,maximum_number_of_ads,position
```

Die Dauer beträgt in Sekunden, mit einer Genauigkeit von 0,001 (Millisekunden); Die Anzahl der Anzeigen ist eine Ganzzahl. Position ist eine der folgenden:
* **n** Keine — keine Anzeige
* **p** Pre-Roll — vor dem Inhalt
* **m** Mid-Roll — innerhalb des Inhalts
* **t** Post-Roll — nach dem Inhalt

`B,60,2,p` stellt beispielsweise eine einminütige Unterbrechung für bis zu 2 Anzeigen vor dem Inhalt dar.

### Inhaltssegment - Kapitel

```
C,duration,number_of_lots
```

Die Dauer beträgt in Sekunden, mit einer Genauigkeit von 0,001 (Millisekunden); Die Anzahl der Lose (Inhaltsabschnitte) ist eine Ganzzahl. `C,300,1` stellt beispielsweise einen einzelnen 5-minütigen Abschnitt des Inhalts dar.