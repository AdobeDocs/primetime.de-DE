---
description: Sie können eine Steuerleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client Live Point.
title: Eine für DVR erweiterte Steuerleiste erstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Eine für DVR verbesserte Steuerleiste erstellen{#construct-a-control-bar-enhanced-for-dvr}

Sie können eine Steuerleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client Live Point.

* Bei VOD ist die Länge des durchsuchbaren Fensters die Dauer des gesamten Assets.
* Beim Live-Streaming wird die Länge des DVR-Fensters (suchbar) als der Zeitraum definiert, der beim Live-Wiedergabefenster beginnt und am Live-Point des Clients endet.

   Der Live-Point des Clients wird berechnet, indem die gepufferte Länge vom Ende des Live-Fensters abgezogen wird. Die Dauer der Zielgruppe ist ein Wert, der größer oder gleich der Maximaldauer eines Fragments im Manifest ist.

   Die Steuerungsleiste für die Live-Wiedergabe unterstützt DVR, indem der Daumen beim Starten der Wiedergabe zunächst am Live-Point des Clients positioniert wird und ein Bereich angezeigt wird, der den Bereich kennzeichnet, in dem die Suche nicht zulässig ist.

Für eine Steuerleiste:

1. hinzufügen eine Überlagerung auf die Steuerleiste, die den Wiedergabebereich darstellt.

1. Überprüfen Sie beim Beginn der Suche, ob sich die gewünschte Suchposition innerhalb des suchbaren Bereichs befindet.
