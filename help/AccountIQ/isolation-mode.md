---
title: Anzeigen von Berichten im Isolationsmodus
description: 'Anzeigen von Berichten im Isolationsmodus für Xfinity '
source-git-commit: afa77dd0d7ffe38d353fed21dc9591b994b11193
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Anzeigen von Berichten im Isolationsmodus {#report-isolation-mode}

Im Isolationsmodus identifizieren MVPDs (z. B. Xfinity) Abonnenten systematisch geräteübergreifend, identifizieren ihre Abonnenten jedoch unterschiedlich, basierend auf den Programmierern, mit denen sie interagieren. Im Standardmodus identifizieren MVPDs Abonnenten konsistent geräteübergreifend, unabhängig von den Programmierern.

Wenn beispielsweise in der folgenden Abbildung ein Abonnent B eines Isolationsmodus-MVPD (z. B. Xfinity) auf den Inhalt zugreift, der von zwei verschiedenen Programmierern mit demselben Gerät bereitgestellt wird, ordnet der MVPD unterschiedliche Kennungen den beiden verschiedenen Zugriffsversuchen zu. Für diese Programmierer (L und M in der Abbildung) und für Konto IQ scheint es, dass es zwei verschiedene Abonnenten gibt, die auf den Inhalt zugreifen. Wenn jedoch bei Standard-MVPD Abonnenten B auf Inhalte zugreift, die von zwei verschiedenen Programmierern bereitgestellt werden, verknüpft der MVPD eine einzige Zugriffskennung für beide Zugriffsversuche. MVPDs (z. B. Xfinity) im Isolationsmodus identifizieren einen Abonnenten nicht konsistent, selbst wenn der Abonnent dasselbe Gerät über verschiedene Programmierer hinweg verwendet.

![](assets/isolation-diff-new.png)

*Abbildung: Isolationsmodus MVPD identifiziert vier verschiedene Abonnenten anstelle von zwei*

Um die Datenverzerrung zu verwalten (da derselbe Abonnent aufgrund des Zugriffs auf verschiedene Programmierer als unterschiedlich identifiziert wird), beschränkt der Isolationsmodus die über einen Programmierer gemeldete Aktivität auf die Aktivität nur in den Anwendungen dieses Programmierers. Beispielsweise sieht Programmierer für den Isolationsmodus im obigen Bild Daten nur basierend auf der Aktivität von Identitäten W und Y, wobei Identitäten X und Z ignoriert werden.

>[!IMPORTANT]
>
> Der Nachteil ist, dass Programmierer L aufgrund von Aktivitäten mit anderen Programmierern als L keine Informationen über Abonnenten A und B weitergeben kann.

Im Isolationsmodus werden alle Berechnungen zum Abrufen der Sharing-Werte und aller zugehörigen Metriken nur mithilfe der Aktivität des Geräte-Streaming aus Anwendungen durchgeführt, die zum ausgewählten Programmierer und zu Kanälen gehören.
Die Bewertungen und Wahrscheinlichkeiten der Freigabe werden nur anhand des Streams berechnet, der von den aktuell ausgewählten Kanälen aus beginnt.

So zeigen Sie Metriken im Isolationsmodus an:

1. Auswählen **Isolationsmodus** von **MVPDs im Segment** und wählen Sie **Auswahl anwenden**.

   ![](assets/xfinity-in-segment.gif)

   *Abbildung: MVPD-Auswahl im Isolationsmodus*

1. Wählen Sie die gewünschten Kanäle aus dem **Kanäle im Segment** und wählen Sie **Auswahl anwenden**. Wählen Sie außerdem eine [Zeitrahmen](/help/AccountIQ/product-concepts.md#granularity-def).

   >[!IMPORTANT]
   >
   >Da die Kontofreigabe bei der Messung für das Streaming über alle Programme von Programmierern relevanter ist, werden im Isolationsmodus niedrigere Sharing-Werte und einige Abweichungen in den Metriken angezeigt.

   ![](assets/aggregate-sharing-isolation.png)

   *Abbildung: Freigeben von Wahrscheinlichkeitsmesswerten im Isolationsmodus*

   Beachten Sie, dass die oben genannten Kennzahlen zeigen, dass nur 6 % aller Konten freigegeben werden. und nur 8 % des Inhalts werden von diesen 8 % konsumiert. Die Kanäle können also ihre Punktzahl im Isolationsmodus mit der anderer MVPDs vergleichen. Daher sollten die Informationen, die mit dem Isolationsmodus abgerufen werden, anders interpretiert werden als die anderen Daten.
