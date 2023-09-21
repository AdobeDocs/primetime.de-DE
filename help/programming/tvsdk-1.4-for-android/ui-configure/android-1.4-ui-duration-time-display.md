---
description: Sie können TVSDK verwenden, um Informationen zu den Medien abzurufen, die Sie in der Suchleiste anzeigen können.
title: Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen{#display-the-duration-current-time-and-remaining-time-of-the-video}

Sie können TVSDK verwenden, um Informationen zu den Medien abzurufen, die Sie in der Suchleiste anzeigen können.

1. Warten Sie, bis Ihr Player den Status VORBEREITET aufweist.
1. Rufen Sie die aktuelle Abspielleistenzeit mit dem `MediaPlayer.getCurrentTime` -Methode.

   Dadurch wird die aktuelle Abspielposition auf der virtuellen Timeline in Millisekunden zurückgegeben. Die Zeit wird relativ zum aufgelösten Stream berechnet, der möglicherweise mehrere Instanzen von alternativen Inhalten enthält, z. B. mehrere Anzeigen oder Werbeunterbrechungen, die in den Haupt-Stream aufgeteilt sind. Bei Live-/linearen Streams befindet sich die zurückgegebene Zeit immer im Bereich des Wiedergabefensters.

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. Rufen Sie den Wiedergabebereich des Streams ab und bestimmen Sie die Dauer.
   1. Verwenden Sie die `mediaPlayer.getPlaybackRange` Methode zum Abrufen des virtuellen Zeitbereichs der Zeitleiste.

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. Analysieren des Zeitraums mit `mediacore.utils.TimeRange`.
   1. Um die Dauer zu bestimmen, subtrahieren Sie den Start vom Ende des Bereichs.

      Dies umfasst die Dauer von zusätzlichem Inhalt, der in den Stream (Anzeigen) eingefügt wird.

      Bei VOD beginnt der Bereich immer mit null und der Endwert entspricht der Summe der Dauer des Hauptinhalts und der Dauer des zusätzlichen Inhalts, der in den Stream (Anzeigen) eingefügt wird.

      Bei einem linearen/Live-Asset stellt der Bereich den Bereich des Wiedergabefensters dar und dieser Bereich ändert sich während der Wiedergabe.

      TVSDK ruft Ihre `onUpdated` Callback , um anzugeben, dass das Medienelement aktualisiert wurde und seine Attribute (einschließlich des Wiedergabebereichs) aktualisiert wurden.

1. Verwenden Sie die verfügbaren Methoden für die `MediaPlayer` und `SeekBar` -Klasse, die im Android-SDK öffentlich verfügbar ist, um die Suchleistenparameter einzurichten.

   Hier ist beispielsweise ein mögliches Layout, das die `SeekBar` und zwei `TextView` -Elemente.

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

   Im folgenden Beispiel wird die `Clock.java` Helper-Klasse als Timer, der im Referenz-Player PrimetimeReference verfügbar ist. Diese Klasse legt einen Ereignis-Listener und Trigger fest und `onTick` -Ereignis jede Sekunde oder einen anderen Timeout-Wert, den Sie angeben können.

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

   Bei jedem Cursor ruft dieses Beispiel die aktuelle Position des Medienplayers ab und aktualisiert die SeekBar. Es verwendet die beiden TextView -Elemente, um die aktuelle Zeit und die Endposition des Wiedergabefelds als numerische Werte zu kennzeichnen.

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
