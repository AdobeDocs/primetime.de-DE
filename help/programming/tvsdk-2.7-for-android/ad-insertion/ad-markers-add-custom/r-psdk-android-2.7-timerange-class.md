---
description: Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.
title: TimeRange-Klasse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# TimeRange-Klasse {#timerange-class}

Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Jede `TimeRange`-Spezifikation im Satz stellt ein Segment in der Wiedergabedauer dar, das intern von TVSDK gepflegt wird und entsprechend als anzeigenbezogener Zeitraum gekennzeichnet werden muss.

Die `TimeRange`-Klasse ist eine einfache Datenstruktur, die die Position des Beginns und die Endposition auf der Zeitleiste offen legt. Diese beiden schreibgeschützten Eigenschaften widerspiegeln die Vorstellung eines Zeitraums in der Wiedergabeschlüssel.

>[!TIP]
>
>Beide Werte werden in Millisekunden angegeben.

Im Folgenden finden Sie eine Zusammenfassung der `TimeRange`-Klasse:

```java
public final class TimeRange {
    // the start/end values are provided at construction time
    public static TimeRange createRange(long begin, long duration) {...} 

    // only getters are available
    public long getBegin() {...} 
    public long getEnd() {...} 
    public long getDuration() {...}
}
```

