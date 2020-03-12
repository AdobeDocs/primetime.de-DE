---
description: Sie können eine Steuerleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client Live Point.
seo-description: Sie können eine Steuerleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client Live Point.
seo-title: Eine für DVR erweiterte Steuerleiste erstellen
title: Eine für DVR erweiterte Steuerleiste erstellen
uuid: 988dcaf5-896d-4da1-8b78-5acf5a317aa3
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Eine für DVR erweiterte Steuerleiste erstellen {#construct-a-control-bar-enhanced-for-dvr}

Sie können eine Steuerleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client Live Point.

* Bei VOD ist die Länge des durchsuchbaren Fensters die Dauer des gesamten Assets.
* Beim Live-Streaming wird die Länge des DVR-Fensters (suchbar) als der Zeitraum definiert, der im Live-Wiedergabefenster Beginn wird und am Live-Point des Clients endet.

   Beachten Sie die folgenden Informationen:

   * Der Live-Point des Clients wird berechnet, indem die gepufferte Länge vom Ende des Live-Fensters abgezogen wird.

      Die Dauer der Zielgruppe ist ein Wert, der größer oder gleich der Maximaldauer eines Fragments im Manifest ist.
   * Der Standardwert ist 10000 ms.
   * Die Steuerungsleiste für die Live-Wiedergabe unterstützt DVR, indem der Daumen beim Starten der Wiedergabe zunächst am Live-Point des Clients positioniert wird und ein Bereich angezeigt wird, der den Bereich kennzeichnet, in dem die Suche nicht zulässig ist.

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. Um eine Steuerleiste mit DVR-Unterstützung zu implementieren, führen Sie die Schritte unter [Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition aus.](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/ui-configure/android-3x-ui-seek-scrub-bar-display.md) mit folgenden Unterschieden:

   * Sie können eine Steuerungsleiste implementieren, die nur für den suchbaren Bereich und nicht für den Wiedergabefeld zugeordnet wird.

      Jede Benutzerinteraktion zur Suche kann im suchbaren Bereich als sicher betrachtet werden.
   * Sie können eine Steuerleiste implementieren, die für den Wiedergabebereich zugeordnet ist, aber auch den suchbaren Bereich anzeigt.

      Für eine Steuerleiste:
   1. Hinzufügen eine Überlagerung auf die Steuerleiste, die den Wiedergabebereich darstellt.
   1. Überprüfen Sie beim Beginn der Suche, ob sich die gewünschte Suchposition innerhalb des suchbaren Bereichs befindet `MediaPlayer.getSeekableRange`.

      Beispiel:

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      Sie können auch den Live-Point des Clients mithilfe der `MediaPlayer.LIVE_POINT` Konstante suchen.

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```
