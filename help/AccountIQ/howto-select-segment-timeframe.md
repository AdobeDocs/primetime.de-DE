---
title: Definieren eines Segments und eines Zeitrahmens
description: Definieren eines Segments und eines Zeitrahmens
source-git-commit: a23de698b073d271df9b04494ff59f5d5a194c9d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Definieren eines Segments und eines Zeitrahmens {#define-segment}

Alle Analysen oder Anzeigen von Berichten in Konto IQ beginnen mit der Definition des Segments und der Auswahl des Zeitrahmens für die Auswertung. [Segment](/help/AccountIQ/product-concepts.md#segmet-def) bezieht sich auf alle Abonnenten oder Viewer, die Ihre Kriterien erfüllen (Abonnieren eines MVPD und Anzeigen bestimmter Kanäle).

![](assets/segment-panel.png)

*Abbildung: Auswahl von Segmenten und Zeitrahmen*

Oben auf allen Berichtseiten in Konto IQ gibt es ein Bedienfeld, in dem das Segment definiert werden kann, indem MVPDs, Kanalprogrammierer sowie Granularität und Zeitrahmen ausgewählt werden.

## Segmentauswahl {#select-segment}

### Auswählen von MVPDs im Segment {#select-segment-mvpds}

So wählen Sie MVPDs aus **MVPDs im Segment** Option:

1. Klicken oder tippen Sie auf **MVPDs im Segment** Dropdown-Option.

   >[!NOTE]
   >
   >**Alle** MVPDs der Branche sind standardmäßig ausgewählt. Von hier aus können Sie einen der **Top-10-MVPDs nach Freigabe der Punktzahl**, **Die 10 MVPDs nach Verwendung**, **Die 10 MVPDs nach Konten** oder einzelne MVPDs. Um jedoch einzelne MVPDs auszuwählen, müssen Sie die Auswahl aufheben **Alle**.

1. Klicken oder tippen Sie auf die gewünschten MVPDs.

   Sie können einen MVPD aus der Auswahl entfernen, indem Sie die Auswahl aufheben.

1. Klicken oder tippen Sie auf **Auswahl anwenden** , damit Ihre Auswahl wirksam wird. Andernfalls verlieren Sie die von Ihnen ausgewählte Auswahl.

   >[!NOTE]
   >
   >Wenn Sie den Isolationsmodus auswählen, kann keiner der anderen MVPDs ausgewählt werden.

### Kanäle im Segment auswählen {#select-segment-channels}

So wählen Sie die gewünschten Programmierkanäle aus dem **Kanäle im Segment** Option:

1. Klicken oder tippen Sie auf **Kanäle im Segment** Dropdown-Option.

   >[!NOTE]
   >
   >**Alle** -Programmierkanäle für Ihr Unternehmen sind standardmäßig ausgewählt. Um einzelne Kanäle oder Programmierer auszuwählen, müssen Sie zunächst die Auswahl aufheben **Alle**.

1. Klicken oder tippen Sie auf die gewünschten Kanäle oder Programmierer.

   Die Listenelemente der obersten Ebene im **Kanäle im Segment** are [Programmierer](/help/AccountIQ/product-concepts.md#programmer-def) Unternehmen und die Listenelemente unter den Programmiernamen sind ihre [channels](/help/AccountIQ/product-concepts.md#channel-def). Sie können entweder einzelne Kanäle unter Programmierern auswählen oder Programmierer auswählen und alle Aktivitäten der Kanäle unter diesem Programmierer sind in den Berichts- und Diagrammergebnissen enthalten.

   ![](assets/programmer-channels.png)

   *Abbildung: In der Kanalauswahl aufgelistete Programmierer und Kanäle*

   >[!IMPORTANT]
   >
   >Die Ergebnisse der Auswahl einzelner Kanäle unter einem Programmierer sind nicht mit denen der Auswahl des Programmierers identisch.
   >
   >
   >Wenn Sie einzelne Kanäle auswählen, werden die Aktivitäten dieser Kanäle in einigen Berichten einzeln aufgeschlüsselt. Wenn Sie jedoch den übergeordneten Programmierer all dieser Kanäle auswählen, werden alle Aktivitäten dieser Kanäle eingeschlossen, aber nicht einzeln in Berichten aufgeschlüsselt.

1. Klicken oder tippen Sie auf **Auswahl anwenden** , damit Ihre Auswahl wirksam wird.

>[!NOTE]
>
>Sie können nicht mehr als 10 Elemente in den MVPD- oder Programmierer-Pulldown-Menüs auswählen.

### Deaktivieren Sie MVPDs und Kanäle. {#deselect-segment-mvpds-channels}

Zusätzlich zur Änderung Ihrer Auswahl im **MVPDs im Segment** und **Kanäle im Segment** Segmentselektoren können Sie die Auswahl der zuvor ausgewählten MVPDs und Kanäle aufheben, indem Sie:

* Auswählen der **Entfernen** Symbol (![Symbol entfernen](assets/remove-icon.png)) in den Namen dieser ausgewählten MVPDs und Kanäle angezeigt, die unter der Segmentauswahl angezeigt werden.

* Sie können auch **Auswahl löschen** um alle zuvor ausgewählten MVPDs oder Kanäle zu entfernen.

![](assets/segment-panel-selection1.png)

*Abbildung: Ausgewählte MVPDs und Kanäle in Segment- und Zeitrahmen-Bedienfeld*

![](assets/segment-panel-selection.png)

*Abbildung: Ausgewählte MVPDs und Kanäle in Segment- und Zeitrahmen-Bedienfeld*

## Granularität und Zeitrahmen-Auswahl {#granularity-timeframe}

So wählen Sie einen Zeitraum für die Auswertung aus:

1. Wählen Sie die **Granularität und Zeitrahmen** Datumsauswahl.

1. Wählen Sie entweder **Woche** oder **Monat** von **Aggregieren nach** -Option, um die Granularität für Ihre Bewertung festzulegen.

   ![](assets/granularity-timeframe-weekwise.png)

   *Abbildung: Datumsauswahl zur Auswahl der Granularität und des Zeitrahmens*

1. Nachdem Sie die Granularität ausgewählt haben, können Sie die Nach-vorne- oder Nach-hinten-Pfeile verwenden, um in der Zeit vorwärts oder rückwärts zu wechseln.

1. Geben Sie einen Zeitraum in der Vergangenheit (in Monat oder Woche basierend auf der ausgewählten Granularität) für die Auswertung an.

1. Auswählen **Auswahl anwenden** , um sicherzustellen, dass Ihre Auswahl wirksam wird.
