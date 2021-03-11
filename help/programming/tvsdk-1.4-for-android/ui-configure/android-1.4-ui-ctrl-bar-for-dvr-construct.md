---
description: Sie können eine Steuerleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client Live Point.
title: Eine für DVR erweiterte Steuerleiste erstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Eine für DVR verbesserte Steuerleiste erstellen{#construct-a-control-bar-enhanced-for-dvr}

Sie können eine Steuerleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client Live Point.

* Bei VOD ist die Länge des durchsuchbaren Fensters die Dauer des gesamten Assets.
* Beim Live-Streaming wird die Länge des DVR-Fensters (suchbar) als der Zeitraum definiert, der beim Live-Wiedergabefenster beginnt und am Live-Point des Clients endet.

   Der Live-Point des Clients wird berechnet, indem die gepufferte Länge vom Ende des Live-Fensters abgezogen wird. Die Dauer der Zielgruppe ist ein Wert, der größer oder gleich der Maximaldauer eines Fragments im Manifest ist.

   Der Standardwert ist 10000 ms.

   Die Steuerungsleiste für die Live-Wiedergabe unterstützt DVR, indem der Daumen beim Starten der Wiedergabe zunächst am Live-Point des Clients positioniert wird und ein Bereich angezeigt wird, der den Bereich kennzeichnet, in dem die Suche nicht zulässig ist.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. Um eine Steuerleiste mit DVR-Unterstützung zu implementieren, führen Sie die Schritte zum Anzeigen einer Suchleiste mit einigen geringfügigen Unterschieden aus:

   * Sie können festlegen, dass eine Steuerleiste implementiert wird, die nur für den suchbaren Bereich und nicht für den Wiedergabebereich zugeordnet wird. Jede Benutzerinteraktion zur Suche kann im suchbaren Bereich als sicher betrachtet werden.
   * Sie können eine Steuerungsleiste implementieren, die für den Wiedergabebereich zugeordnet ist, aber auch den suchbaren Bereich anzeigt.

      Für eine Steuerleiste:
   1. hinzufügen eine Überlagerung auf die Steuerleiste, die den Wiedergabebereich darstellt.
   1. Wenn der Beginn die Suche durchführt, prüfen Sie, ob die gewünschte Suchposition innerhalb des suchbaren Bereichs liegt, indem Sie `MediaPlayer.getSeekableRange` verwenden.

      Beispiel:

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      Sie können auch mit der Konstante `MediaPlayer.LIVE_POINT` nach dem Live-Point des Clients suchen.

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```
