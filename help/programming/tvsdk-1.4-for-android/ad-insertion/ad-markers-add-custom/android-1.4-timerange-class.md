---
description: Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.
seo-description: Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.
seo-title: TimeRange-Klasse
title: TimeRange-Klasse
uuid: adf4f1ad-6b3b-48ac-a388-ee1fd54f770b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# TimeRange-Klasse{#timerange-class}

Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen, die Zeitleistensegmente darstellen, an TVSDK weiterleiten.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Jede TimeRange-Spezifikation im Satz stellt ein Segment in der Wiedergabeschlüssel dar, das intern von TVSDK verwaltet wird und entsprechend als anzeigenbezogene Zeitspanne gekennzeichnet werden muss.

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

