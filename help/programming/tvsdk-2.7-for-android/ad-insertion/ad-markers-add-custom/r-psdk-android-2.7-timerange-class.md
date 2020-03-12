---
description: Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.
seo-description: Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.
seo-title: TimeRange-Klasse
title: TimeRange-Klasse
uuid: e5a176af-29b9-4aa6-848e-5aba7988584b
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# TimeRange-Klasse {#timerange-class}

Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Jede `TimeRange` Spezifikation im Satz stellt ein Segment in der Wiedergabedauer dar, das intern von TVSDK gepflegt wird und entsprechend als anzeigenbezogener Zeitraum gekennzeichnet werden muss.

Die `TimeRange` Klasse ist eine einfache Datenstruktur, die die Position des Beginns und die Endposition auf der Zeitleiste offen legt. Diese beiden schreibgeschützten Eigenschaften widerspiegeln die Vorstellung eines Zeitraums in der Wiedergabeschlüssel.

>[!TIP]
>
>Beide Werte werden in Millisekunden angegeben.

Im Folgenden finden Sie eine Zusammenfassung der `TimeRange` Klasse:

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

