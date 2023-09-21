---
description: Sie können eine Kontrollleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client-Live-Points.
title: Erstellen einer für DVR erweiterten Steuerleiste
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Erstellen einer für DVR erweiterten Steuerleiste {#construct-a-control-bar-enhanced-for-dvr}

Sie können eine Kontrollleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client-Live-Points.

* Bei VOD entspricht die Länge des durchsuchbaren Fensters der Dauer des gesamten Assets.
* Beim Live-Streaming ist die Länge des DVR-Fensters (suchbar) als der Zeitraum definiert, der am Live-Wiedergabefenster beginnt und am Client-Live-Point endet.

  Beachten Sie die folgenden Informationen:

   * Der Client-Live-Point wird berechnet, indem die gepufferte Länge vom Ende des Live-Fensters abgezogen wird.

     Die Zieldauer ist ein Wert, der größer oder gleich der maximalen Dauer eines Fragments im Manifest ist.
   * Der Standardwert ist 10000 ms.
   * Die Steuerleiste für die Live-Wiedergabe unterstützt DVR, indem sie beim Start der Wiedergabe den Daumen beim Start des Client-Live-Punkts platziert und einen Bereich anzeigt, der den Bereich markiert, in dem die Suche nicht zulässig ist.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width="684"}

1. Um eine Kontrollleiste mit DVR-Unterstützung zu implementieren, führen Sie die Schritte unter [Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition ...](../../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md) mit den folgenden Unterschieden:

   * Sie können eine Kontrollleiste implementieren, die nur für den suchbaren Bereich und nicht für den Wiedergabefeld zugeordnet ist.

     Jede Benutzerinteraktion für die Suche kann im suchbaren Bereich als sicher betrachtet werden.
   * Sie können eine Kontrollleiste implementieren, die dem Wiedergabefeld zugeordnet ist, aber auch den suchbaren Bereich anzeigt.

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
