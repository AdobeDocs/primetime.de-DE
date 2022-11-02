---
description: Sie können eine Kontrollleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client-Live-Points.
title: Erstellen Sie eine für DVR erweiterte Steuerleiste.
exl-id: a812f2d5-f1ee-4df6-9cc7-e39f55ec26f1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Erstellen Sie eine für DVR erweiterte Steuerleiste.{#construct-a-control-bar-enhanced-for-dvr}

Sie können eine Kontrollleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client-Live-Points.

* Bei VOD entspricht die Länge des durchsuchbaren Fensters der Dauer des gesamten Assets.
* Beim Live-Streaming ist die Länge des DVR-Fensters (suchbar) als der Zeitraum definiert, der beim Live-Wiedergabefenster beginnt und am Client-Live-Point endet.

   Der Client-Live-Point wird berechnet, indem die gepufferte Länge vom Ende des Live-Fensters abgezogen wird. Die Zieldauer ist ein Wert, der größer oder gleich der maximalen Dauer eines Fragments im Manifest ist.

   Der Standardwert ist 10000 ms.

   Die Steuerleiste für die Live-Wiedergabe unterstützt DVR, indem sie beim Start der Wiedergabe den Daumen beim Start des Client-Live-Punkts platziert und einen Bereich anzeigt, der den Bereich markiert, in dem die Suche nicht zulässig ist.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width="684"}

1. Um eine Kontrollleiste mit DVR-Unterstützung zu implementieren, führen Sie die Schritte zum Anzeigen einer Suchleiste mit einigen geringfügigen Unterschieden aus:

   * Sie können festlegen, dass eine Kontrollleiste implementiert wird, die nur für den suchbaren Bereich und nicht für den Wiedergabefeld zugeordnet ist. Jede Benutzerinteraktion für die Suche kann im suchbaren Bereich als sicher betrachtet werden.
   * Sie können eine Kontrollleiste implementieren, die für den Wiedergabefeld zugeordnet ist, aber auch den suchbaren Bereich anzeigt.

      Für eine Steuerleiste:
   1. Fügen Sie der Steuerleiste eine Überlagerung hinzu, die den Wiedergabebereich darstellt.
   1. Wenn der Benutzer mit der Suche beginnt, überprüfen Sie, ob sich die gewünschte Suchposition innerhalb des suchbaren Bereichs befindet, indem Sie `MediaPlayer.getSeekableRange`.

      Beispiel:

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      Sie können auch mithilfe der `MediaPlayer.LIVE_POINT` Konstante.

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```
