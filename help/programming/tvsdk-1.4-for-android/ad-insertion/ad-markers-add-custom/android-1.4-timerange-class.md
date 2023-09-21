---
description: Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen übergeben, die Zeitleistensegmente für TVSDK darstellen.
title: TimeRange-Klasse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# TimeRange-Klasse{#timerange-class}

Mit benutzerdefinierten Anzeigenmarken können Sie eine Reihe von TimeRange-Spezifikationen übergeben, die Zeitleistensegmente für TVSDK darstellen.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Jede TimeRange-Spezifikation im Satz stellt ein Segment auf der Wiedergabescheitleiste dar, das intern von TVSDK gepflegt wird und entsprechend als anzeigenbezogenen Zeitraum gekennzeichnet werden muss.

Die `TimeRange` -Klasse ist eine einfache Datenstruktur, die die Anfangs- und Endposition auf der Timeline anzeigt. Diese beiden schreibgeschützten Eigenschaften widerspiegeln die Idee eines Zeitraums in der Wiedergabe-Timeline.

>[!TIP]
>
>Beide Werte werden in Millisekunden ausgedrückt.

Im Folgenden finden Sie eine Zusammenfassung der `TimeRange` -Klasse:

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
