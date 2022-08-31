---
title: Dashboard "Konto-IQ"
description: Das Dashboard hilft, die Instanzen der Kennwortfreigabe zu identifizieren, indem es eine breite Palette von Abonnentendaten analysiert.
exl-id: 616da2a5-c9fe-40ea-90cf-f565bc13e764
source-git-commit: a015cf059c599c043f03b981eed640fbdbffc27b
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Das Dashboard {#dashboard}

Das Dashboard fasst Daten in einer Sammlung von Diagrammen und Berichten zusammen und bietet so einen allgemeinen Überblick über den Umfang und die Auswirkungen der Kontofreigabe. Es bietet eine einzelne Seite, die die wichtigsten Berichte und Metriken aus Konto IQ enthält.

![Dashboard von Konto-IQ](assets/dashboard-capture.png)


*Abbildung: Das Dashboard*

## Durchschnittliche Teilungsbewertung - aggregiert für das aktuelle Segment {#aggregated-sharing}

Das Bedienfeld &quot;Aggregierte Sharing-Bewertung&quot;bietet eine Zusammenfassung der Menge und Auswirkung der Freigabe in Bezug auf Konten und Streaming-Volumen.

Die Werte helfen Ihnen dabei, das Ausmaß der Weitergabe von Anmeldedaten durch Ihre Abonnenten zu verstehen und liefern so ein Maß für die Notwendigkeit, entsprechend zu handeln.

![](assets/aggregate-sharing-score.png)


*Abbildung: Bedienfeld &quot;Durchschnittliche Teilungsbewertung&quot;- für das aktuelle Segment aggregiert*

Die folgenden drei Metriken sind Komponenten der durchschnittlichen Sharing-Bewertung.

### Teilungsebene {#sharing-level}

Der Freigabewert zeigt den Prozentsatz aller Abonnentenkonten (im definierten Segment) an, die während des ausgewählten Zeitraums freigegeben werden.

Ein Wert, der auf der Grundlage der durchschnittlichen Freigabewahrscheinlichkeit berechnet wird, die für jedes Konto in der Gruppe ausgewählter MVPDs berechnet wurde, das während des ausgewählten Zeitraums aus einem der ausgewählten Programmierkanäle gestreamt hat.

![](assets/sharing-level.png)


*Abbildung: Teilungsebene*

Der Trend -Indikator zeigt die prozentuale Änderung des Werts der Metrik im Vergleich zum vorherigen Zeitrahmen an.

### Nutzung durch freigegebene Konten {#usage-from-shared-accounts}

Diese Messung gibt an, welcher Anteil der Nutzung aller Abonnentenkonten aus den gemeinsam genutzten Konten für das definierte Segment und den definierten Zeitraum stammt. Die Messung markiert die Nutzungsbereiche (von gemeinsam genutzten Konten) im Maßstab von 0 bis 100 %. Diese Bereiche - Niedrig, Mittel, Hoch und Abnormal - basieren auf dem Branchendurchschnitt.

Sie können auch den Trend -Indikator sehen, der einen Anstieg oder Rückgang der Nutzung von freigegebenen Konten im Vergleich zum vorherigen Zeitraum darstellt.

![](assets/usage-4mshared-accounts.png)


*Abbildung: Nutzung durch freigegebene Konten*

### Gesamte Teilungsbewertung {#overall-sharing-score}

Die Gesamtbewertung für die Freigabe besteht aus Sharing-Werten wie &quot;Sharing Level&quot;und &quot;z Usage from shared accounts&quot;.

Sie bietet einen Wert, der die relativen Auswirkungen der Freigabe im Vergleich zur Branche widerspiegelt. Der Zweck ist ähnlich dem eines Kreditwerts und fasst die Situation mit einer einzelnen Zahl zusammen. Aber in diesem Fall gilt: Je höher die Zahl, desto größer ist der potenzielle Schaden.

![](assets/overall-sharing-score.png)


*Abbildung: Gesamte Teilungsbewertung*

<!--### MVPDs in segment {#mvpd-in-segment}

It is a table of risk indices and accounts totals for the top MVPDs ranked by overall usage or account sharing.

![](assets/mvpds-in-segment.png)-->

## Gesamtwert der branchenweiten Freigabe für MVPDs {#top-mvpds}

Diese Tabelle bietet einen vergleichenden Überblick über die verschiedenen aggregierten Sharing-Werte für die MVPDs im Segment.

>[!NOTE]
>
>In dieser Tabelle werden die gesamten Branchendaten zu Vergleichszwecken verwendet, nicht aber die Daten, die von diesen MVPDs im Segment dargestellt werden.

![](assets/top-mvpds.png)


*Abbildung: Top-MVPDs im Segment nach Gesamtwert*

## Teilungsbewertung nach Kanälen und MVPDs {#sharin-score-by-channels-and-mvpds}

Diese Tabelle bietet einen vergleichenden Überblick über die Freigabe von Werten der ausgewählten Kanäle für die MVPDs im aktuellen Segment.

![](assets/sharing-scores-by-channels-mvpds.png)


*Abbildung: Teilen von Bewertungen nach Kanälen und MVPDs*

## Wahrscheinlichkeit der Kontofreigabe {#accounts-sharing-probability}

Dieses Diagramm teilt in Bereiche mit Wahrscheinlichkeitsquintilien von sehr niedrig (0-20%) bis sehr hoch (80=100%) auf.

>[!NOTE]
>
>Das Balkendiagramm verwendet eine logarithmische Skala.


![](assets/dashboard-ac-sharing-prob.png)


*Abbildung: Anzahl und Prozentsatz der Abonnentenkonten in verschiedenen Wahrscheinlichkeitsbereichen für die Freigabe*

## Anzahl der Konten und Nutzung nach Freigabe der Wahrscheinlichkeitsstufe {#number-of-accounts-usage-sharing-probability}

Dieses Bedienfeld bietet eine tabellarische Ansicht von Konten, die in Bereiche mit Wahrscheinlichkeitsquintilien aufgeteilt sind, die von sehr niedrig (0-20 %) bis sehr hoch (80-100 %) mit der zugehörigen Nutzung der einzelnen Quintile aus freigegebenen Konten reichen.

![](assets/no-acc-usage-prob-level.png)


*Abbildung: Anzahl der Konten, Trends und Verwendungen, die in verschiedene Wahrscheinlichkeitsbereiche fallen*



<!--
+++Dashboard for programmers

![dashboard of account IQ](assets/dashboard-capture.png)


*Figure: The dashboard*

## Average sharing score - aggregated for the current segment {#aggregated-sharing}

The Aggregated Sharing Score panel provides a top line readout summarizing the quantity and impact of sharing in terms of accounts and streaming volume.

The values help you understand the magnitude of credential sharing by your subscribers, hence providing a measure of the need to act upon it.

![](assets/aggregate-sharing-score.png)


*Figure: Average sharing score panel - aggregated for the current segment*

The following three metrics are components of the Average Sharing Score.

### Sharing level {#sharing-level}

The sharing level gauge shows the percentage of all your subscriber accounts (in the defined segment) that are shared, during the selected time frame.  

A value calculated based on an average of the sharing probability computed for every account in the set of selected MVPDs that has streamed from a one of the selected programmer channels during the selected time frame.

![](assets/sharing-level.png)


*Figure: Sharing level*

The Trend indicator shows the percentage change in the value of the metric in from the previous time frame.

### Usage from shared accounts {#usage-from-shared-accounts}

This gauge indicates what percent of the usage of all the subscriber accounts is from the shared accounts for the defined segment and time period. The gauge marks the ranges of usage (from shared accounts) on the scale of 0 to 100%. These ranges—named Low, Medium, High, and Abnormal—are based on the industry average.

You can also see the Trend indicator, which depicts a rise or fall in the usage from shared accounts as compared to the previous time frame.

![](assets/usage-4mshared-accounts.png)


*Figure: Usage from shared accounts*

### Overall sharing score {#overall-sharing-score}

Overall sharing score is composite of sharing scores including “Sharing level” and “z Usage from shared accounts”.

It provides a value meant to reflect the relative impact of sharing when compared to the industry. It’s purpose is similar to that of a credit score, summarizing the situation with a single number. But in this case, the higher the number the greater the potential harm.

![](assets/overall-sharing-score.png)


*Figure: Overall sharing score*

<!--### MVPDs in segment {#mvpd-in-segment}

It is a table of risk indices and accounts totals for the top MVPDs ranked by overall usage or account sharing.

![](assets/mvpds-in-segment.png)

### Industrywide overall sharing scores for MVPDs {#top-mvpds}

This table provides a comparative view of the different Aggregated Sharing Scores for the MVPDs in the segment.

>[!NOTE]
>
>This table uses overall industry data for comparative purposes, not the data represented by those MVPDs in the segment.

![](assets/top-mvpds.png)


*Figure: Top MVPDs in segment by overall score*

### Sharing score by channels and MVPDs {#sharin-score-by-channels-and-mvpds}

This table provides a comparative view of sharing scores of the selected channels for the MVPDs in the current segment.

![](assets/sharing-scores-by-channels-mvpds.png)


*Figure: Sharing scores by channels and MVPDs*

### Accounts sharing probability {#accounts-sharing-probability}

This chart partitions accounts into ranges of sharing probability quintiles from very low (0-20%) to very high (80=100%).

>[!NOTE]
>
>The bar graph uses a logarithmic scale.


![](assets/dashboard-ac-sharing-prob.png)


*Figure: Numbers and percentages of subscriber accounts in different sharing probability ranges*

### Number of accounts and usage by sharing probability level {#number-of-accounts-usage-sharing-probability}

This panel provides tabular view of  accounts partitioned into ranges of sharing probability quintiles from very low (0-20%) to very high (80-100%) with each quintile’s associated usage from shared accounts.

![](assets/no-acc-usage-prob-level.png)


*Figure: Number of accounts, trends, and usages falling in various probability ranges*

+++


+++Dashboard for MVPDs
The dashboard for MVPD users is slightly different from those of the programmer users.

![](assets/dashboard-mvpd.png)


*Figure: MVPD's Dashboard*

## Top programmers in segment by overall sharing score {#}

![](assets/top-programmers-panel.png)


*Figure: Panel showing top programmers in a segment*
+++


+++Dashboard for MVPDs
The dashboard for MVPD users is slightly different from those of the programmer users.

![](assets/dashboard-mvpd.png)


*Figure: MVPD's Dashboard*

## Top programmers in segment by overall sharing score {#}


![](assets/top-programmers-panel.png)


*Figure: Panel showing top programmers in a segment*
+++
-->