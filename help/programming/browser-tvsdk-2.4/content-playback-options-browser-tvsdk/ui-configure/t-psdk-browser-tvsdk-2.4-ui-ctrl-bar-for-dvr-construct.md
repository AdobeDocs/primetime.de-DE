---
description: Sie können eine Kontrollleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client-Live-Points.
title: Erstellen einer für DVR erweiterten Steuerleiste
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Erstellen einer für DVR erweiterten Steuerleiste{#construct-a-control-bar-enhanced-for-dvr}

Sie können eine Kontrollleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client-Live-Points.

* Bei VOD entspricht die Länge des durchsuchbaren Fensters der Dauer des gesamten Assets.
* Beim Live-Streaming ist die Länge des DVR-Fensters (suchbar) als der Zeitraum definiert, der beim Live-Wiedergabefenster beginnt und am Client-Live-Point endet.

  Der Client-Live-Point wird berechnet, indem die gepufferte Länge vom Ende des Live-Fensters abgezogen wird. Die Zieldauer ist ein Wert, der größer oder gleich der maximalen Dauer eines Fragments im Manifest ist.

  Die Steuerleiste für die Live-Wiedergabe unterstützt DVR, indem sie beim Start der Wiedergabe den Daumen beim Start des Client-Live-Punkts platziert und einen Bereich anzeigt, der den Bereich markiert, in dem die Suche nicht zulässig ist.

Für eine Steuerleiste:

1. Fügen Sie der Steuerleiste eine Überlagerung hinzu, die den Wiedergabebereich darstellt.

1. Wenn der Benutzer mit der Suche beginnt, überprüfen Sie, ob sich die gewünschte Suchposition innerhalb des suchbaren Bereichs befindet.
