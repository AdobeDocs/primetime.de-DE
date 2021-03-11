---
description: Sie können TVSDK verwenden, um Informationen über die Medien abzurufen, die Sie in der Suchleiste anzeigen können.
title: Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Dauer, aktuelle Zeit und verbleibende Zeit des Videos{#display-the-duration-current-time-and-remaining-time-of-the-video} anzeigen

Sie können TVSDK verwenden, um Informationen über die Medien abzurufen, die Sie in der Suchleiste anzeigen können.

1. Warten Sie, bis Ihr Spieler den Status &quot;VORBEREITT&quot;hat.
1. Rufen Sie die aktuelle Abspielposition mit der `MediaPlayer.getCurrentTime`-Methode ab.

   Dadurch wird die aktuelle Abspielposition auf der virtuellen Zeitleiste in Millisekunden zurückgegeben. Die Zeit wird relativ zum aufgelösten Stream berechnet, der mehrere Instanzen alternativen Inhalts enthalten kann, z. B. mehrere Anzeigen oder Werbeunterbrechungen, die in den Hauptstrom kopiert werden. Bei Live-/linearen Streams liegt die zurückgegebene Zeit immer im Bereich des Wiedergabefensters.

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. Rufen Sie den Wiedergabebereich des Streams ab und bestimmen Sie die Dauer.
   1. Verwenden Sie die `mediaPlayer.getPlaybackRange`-Methode, um den virtuellen Zeitleistenzeitbereich abzurufen.

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. Analysieren Sie den Zeitraum mit `mediacore.utils.TimeRange`.
   1. Um die Dauer zu bestimmen, ziehen Sie den Beginn vom Ende des Bereichs ab.

      Dies umfasst die Dauer zusätzlicher Inhalte, die in den Stream (Anzeigen) eingefügt werden.

      Bei VOD beginnt der Bereich immer mit null und der Endwert entspricht der Summe der Dauer des Hauptinhalts und der Dauer des zusätzlichen Inhalts, der in den Stream eingefügt wird (Anzeigen).

      Bei einem linearen/Live-Asset steht der Bereich für den Bereich des Wiedergabefensters, und dieser Bereich ändert sich während der Wiedergabe.

      TVSDK ruft Ihren `onUpdated`-Rückruf auf, um anzugeben, dass das Medienelement aktualisiert wurde und seine Attribute (einschließlich des Wiedergabebereichs) aktualisiert wurden.

1. Verwenden Sie die für die Klassen `MediaPlayer` und `SeekBar` verfügbaren Methoden, die im Android-SDK öffentlich verfügbar sind, um die Suchleistenparameter einzurichten.

   Hier ist beispielsweise ein mögliches Layout, das die Elemente `SeekBar` und `TextView` enthält.

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

1. Verwenden Sie einen Timer, um die aktuelle Zeit regelmäßig abzurufen und die SeekBar zu aktualisieren.

   Im folgenden Beispiel wird die Helper-Klasse `Clock.java` als Timer verwendet, die im Referenz-Player PrimetimeReference verfügbar ist. Diese Klasse setzt jeden Ereignis-Listener und Trigger ein `onTick`-Ereignis oder einen anderen Timeout-Wert, den Sie angeben können.

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
   @Override 
   public void onTick(String name) { 
       // Timer event is received. Update the SeekBar here. 
   } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   Bei jedem Cursor wird in diesem Beispiel die aktuelle Position des Medienplayers abgerufen und die SeekBar aktualisiert. Es verwendet die beiden TextView-Elemente, um die aktuelle Zeit und die Endposition des Wiedergabebereichs als numerische Werte zu kennzeichnen.

   ```java
   @Override 
   public void onTick(String name) { 
   if (mediaPlayer != null && mediaPlayer.getStatus() == PlayerState.PLAYING) { 
       handler.post(new Runnable() { 
           @Override 
           public void run() { 
               seekBar.setProgress((int)  
                    mediaPlayer.getCurrentTime()); 
               currentTimeText.setText(timeStampToText( 
                  mediaPlayer.getCurrentTime())); 
               totalTimeText.setText(timeStampToText( 
                   mediaPlayer.getPlaybackRange().getEnd())); 
           } 
       }); 
   } 
   }
   ```

