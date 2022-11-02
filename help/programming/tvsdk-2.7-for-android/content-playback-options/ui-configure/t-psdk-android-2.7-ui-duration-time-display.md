---
description: Sie können TVSDK verwenden, um Informationen über die Position des Players in den Medien abzurufen und in der Suchleiste anzuzeigen.
title: Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen
exl-id: d9832f19-c2d1-413a-b094-091052912c96
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen {#display-the-duration-current-time-and-remaining-time-of-the-video}

Sie können TVSDK verwenden, um Informationen über die Position des Players in den Medien abzurufen und in der Suchleiste anzuzeigen.

1. Warten Sie, bis der Player mindestens den Status VORBEREITET aufweist.
1. Rufen Sie die aktuelle Abspielleistenzeit mithilfe der `MediaPlayer.getCurrentTime` -Methode.

   Dadurch wird die aktuelle Abspielposition auf der virtuellen Timeline in Millisekunden zurückgegeben. Die Zeit wird relativ zum aufgelösten Stream berechnet, der möglicherweise mehrere Instanzen von alternativen Inhalten enthält, z. B. mehrere Anzeigen oder Werbeunterbrechungen, die in den Haupt-Stream aufgeteilt sind. Bei Live-/linearen Streams befindet sich die zurückgegebene Zeit immer im Bereich des Wiedergabefensters.

   ```java
   long getCurrentTime() throws MediaPlayerException;
   ```

1. Rufen Sie den Wiedergabebereich des Streams ab und bestimmen Sie die Dauer.
   1. Verwenden Sie die `MediaPlayer.getPlaybackRange` -Methode, um den virtuellen Zeitbereich der Zeitleiste abzurufen.

      ```java
      TimeRange getPlaybackRange() throws MediaPlayerException;
      ```

   1. Verwenden Sie die `MediaPlayer.getPlaybackRange` -Methode, um den virtuellen Zeitbereich der Zeitleiste abzurufen.

      * Bei VOD beginnt der Bereich immer mit null und der Endwert entspricht der Summe der Dauer des Hauptinhalts und der Dauer des zusätzlichen Inhalts im Stream (Anzeigen).
      * Bei einem linearen/Live-Asset stellt der Bereich den Bereich des Wiedergabefensters dar. Dieser Bereich ändert sich während der Wiedergabe.

         TVSDK ruft die `ITEM_Updated` Callback , um anzugeben, dass das Medienelement aktualisiert wurde und seine Attribute, einschließlich des Wiedergabebereichs, aktualisiert wurden.

1. Verwenden Sie die Methoden, die unter `MediaPlayer` und auf `SeekBar` -Klasse im Android-SDK verwenden, um die Suchleistenparameter einzurichten.

   Hier ist beispielsweise ein mögliches Layout, das die Suchleiste und zwei `TextView` -Elemente.

   ```xml
   <LinearLayout 
    android:id="@+id/controlBarLayout" 
    android:layout_width="match_parent" 
    android:layout_height="wrap_content" 
    android:layout_alignParentBottom="true" 
    android:background="@android:color/black" 
    android:orientation="horizontal" > 
    <TextView 
       android:id="@+id/playerCurrentTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
    <SeekBar 
       android:id="@+id/playerSeekBar" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_weight="1" /> 
    <TextView 
       android:id="@+id/playerTotalTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
   </LinearLayout>
   ```

1. Verwenden Sie einen Timer, um die aktuelle Zeit regelmäßig abzurufen und die Suchleiste zu aktualisieren, wie in der Abbildung dargestellt:

   <!--<a id="fig_689CEDDD02094C0C8E91C5195F8EAD3F"></a>-->

   ![](assets/seek-bar.jpg){width="477.000pt"}

   Im folgenden Beispiel wird die `Clock.java` Helper-Klasse, verfügbar in `ReferencePlayer`, als Timer. Diese Klasse legt einen Ereignis-Listener und Trigger fest und `onTick` -Ereignis jede Sekunde oder einen anderen Timeout-Wert, den Sie angeben können.

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           // Timer event is received. Update the seek bar here. 
       } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   Bei jedem Cursor ruft dieses Beispiel die aktuelle Position des Medienplayers ab und aktualisiert die Suchleiste. Es verwendet die beiden `TextView` -Elemente, um die aktuelle Zeit und die Endposition des Wiedergabebereichs als numerische Werte zu kennzeichnen.

   ```java
   @Override 
   public void onTick(String name) { 
       if (mediaPlayer != null &&  
         mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
           handler.post(new Runnable() { 
               @Override 
               public void run() { 
                   seekBar.setProgress((int) mediaPlayer.getCurrentTime()); 
                   currentTimeText.setText(timeStampToText(mediaPlayer.getCurrentTime())); 
                   totalTimeText.setText(timeStampToText(mediaPlayer.getPlaybackRange().getEnd())); 
               } 
           }); 
       } 
   } 
   ```
