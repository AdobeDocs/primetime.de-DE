---
description: Sie können TVSDK verwenden, um Informationen über die Position des Players in den Medien abzurufen und sie in der Suchleiste anzuzeigen.
title: Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Dauer, aktuelle Zeit und verbleibende Zeit des Videos {#display-the-duration-current-time-and-remaining-time-of-the-video} anzeigen

Sie können TVSDK verwenden, um Informationen über die Position des Players in den Medien abzurufen und sie in der Suchleiste anzuzeigen.

1. Warten Sie, bis der Player mindestens den Status &quot;VORBEREITT&quot;aufweist.
1. Rufen Sie die aktuelle Abspielposition mit der `MediaPlayer.getCurrentTime`-Methode ab.

   Dadurch wird die aktuelle Abspielposition auf der virtuellen Zeitleiste in Millisekunden zurückgegeben. Die Zeit wird relativ zum aufgelösten Stream berechnet, der mehrere Instanzen alternativen Inhalts enthalten kann, z. B. mehrere Anzeigen oder Werbeunterbrechungen, die in den Hauptstrom kopiert werden. Bei Live-/linearen Streams liegt die zurückgegebene Zeit immer im Bereich des Wiedergabefensters.

   ```java
   long getCurrentTime() throws MediaPlayerException;
   ```

1. Rufen Sie den Wiedergabebereich des Streams ab und bestimmen Sie die Dauer.
   1. Verwenden Sie die `MediaPlayer.getPlaybackRange`-Methode, um den virtuellen Zeitleistenzeitbereich abzurufen.

      ```java
      TimeRange getPlaybackRange() throws MediaPlayerException;
      ```

   1. Verwenden Sie die `MediaPlayer.getPlaybackRange`-Methode, um den virtuellen Zeitleistenzeitbereich abzurufen.

      * Bei VOD beginnt der Bereich immer mit null und der Endwert entspricht der Summe der Dauer des Hauptinhalts und der Dauer des zusätzlichen Inhalts im Stream (Anzeigen).
      * Bei einem linearen/Live-Asset entspricht der Bereich dem Bereich des Wiedergabefensters. Dieser Bereich ändert sich während der Wiedergabe.

         TVSDK ruft den Rückruf `ITEM_Updated` auf, um anzugeben, dass das Medienelement aktualisiert wurde und seine Attribute, einschließlich des Wiedergabebereichs, aktualisiert wurden.

1. Verwenden Sie die Methoden, die für `MediaPlayer` und für die `SeekBar`-Klasse im Android SDK verfügbar sind, um die Suchleistenparameter einzurichten.

   Hier ist beispielsweise ein mögliches Layout, das die Suchleiste und zwei `TextView`-Elemente enthält.

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

1. Verwenden Sie einen Timer, um in regelmäßigen Abständen die aktuelle Zeit abzurufen und die Suchleiste zu aktualisieren, wie in der Abbildung dargestellt:

   <!--<a id="fig_689CEDDD02094C0C8E91C5195F8EAD3F"></a>-->

   ![](assets/seek-bar.jpg){width=&quot;477.000pt&quot;}

   Im folgenden Beispiel wird die Helper-Klasse `Clock.java` verwendet, die in `ReferencePlayer` verfügbar ist, als Timer. Diese Klasse setzt jeden Ereignis-Listener und Trigger ein `onTick`-Ereignis oder einen anderen Timeout-Wert, den Sie angeben können.

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

   Bei jedem Cursor wird in diesem Beispiel die aktuelle Position des Medienplayers abgerufen und die Suchleiste aktualisiert. Es verwendet die beiden Elemente `TextView`, um die aktuelle Zeit und die Endposition des Wiedergabebereichs als numerische Werte zu kennzeichnen.

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

