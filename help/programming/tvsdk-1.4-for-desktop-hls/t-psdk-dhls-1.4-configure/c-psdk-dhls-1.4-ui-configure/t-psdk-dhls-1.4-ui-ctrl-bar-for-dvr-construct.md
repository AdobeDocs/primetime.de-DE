---
description: Sie können eine Kontrollleiste mit DVR-Unterstützung für VOD und Live-Streaming implementieren. DVR-Unterstützung beinhaltet das Konzept eines durchsuchbaren Fensters und des Client-Live-Points.
title: Erstellen Sie eine für DVR erweiterte Steuerleiste.
exl-id: 8e70f03c-880a-48c5-8728-a4b967c19925
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '321'
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
   1. Wenn der Benutzer mit der Suche beginnt, überprüfen Sie mithilfe der `MediaPlayer.seekableRange` -Eigenschaft.

      Beispiel:

      ```
      var desiredPosition:Number = // TODO : choose a value 
      
      private function onStatusChange(event:MediaPlayerStatusChangeEvent):void { 
          switch(event.status) { 
              case MediaPlayerStatus.PREPARED: 
                  _mediaPlayer.prepareToPlay(desiredPosition); 
          } 
      }
      ```

      Sie können auch mithilfe der `MediaPlayer.LIVE_POINT` Konstante.

      ```
      private function onSeekToLiveClick(event:MouseEvent):void { 
          _player.seek(DefaultMediaPlayer.LIVE_POINT); 
      }
      ```
