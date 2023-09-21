---
description: TVSDK unterstützt das Suchen nach einer bestimmten Position (Uhrzeit), an der der Stream eine gleitende Fensterwiedergabeliste ist, in Video On Demand (VOD) und Live-Streams.
title: Anzeigen einer Suchscrubb-Leiste mit der aktuellen Wiedergabeposition
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Anzeigen einer Suchscrubb-Leiste mit der aktuellen Wiedergabeposition {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK unterstützt das Suchen nach einer bestimmten Position (Uhrzeit), an der der Stream eine gleitende Fensterwiedergabeliste ist, in Video On Demand (VOD) und Live-Streams.

>[!TIP]
>
>Die Suche in einem Live-Stream ist nur für DVR erlaubt.

1. Richten Sie Rückrufe für die Suche ein.

   Die Suche ist asynchron, sodass TVSDK die folgenden suchbezogenen Ereignisse sendet:

   * `MediaPlayerEvent.SEEK_BEGIN`, wo die Suche beginnt.
   * `MediaPlayerEvent.SEEK_END`, wobei die Suche erfolgreich ist.
   * `MediaPlayerEvent.OPERATION_FAILED`, wo die Suche fehlgeschlagen ist.

1. Warten Sie, bis der Player einen gültigen Status für die Suche aufweist.

   Die gültigen Status sind PREPARED, COMPLETE, PAUSED und PLAYING.
1. Verwenden Sie den nativen `SeekBar` auf `OnSeekBarChangeListener`, der festlegt, wann der Benutzer scrubbt.
1. Übergeben Sie die angeforderte Suchposition (Millisekunden) an die `MediaPlayer.seek` -Methode.

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   Sie können nur in der suchbaren Dauer des Assets suchen. Bei Video On Demand ist dies von 0 bis zur Dauer des Assets.

   >[!TIP]
   >
   >Durch diesen Schritt wird der Abspielkopf an eine neue Position im Stream verschoben, die endgültige berechnete Position kann jedoch von der angegebenen Suchposition abweichen.

1. Suchen Sie nach `MediaPlayerEvent.OPERATION_FAILED` und geeignete Maßnahmen ergreifen.

   Dieses Ereignis übergibt die entsprechende Warnung. Ihre Anwendung legt fest, wie der Vorgang fortgesetzt werden soll. Zu den Optionen gehören der erneute Versuch der Suche oder die Fortsetzung der Wiedergabe von der vorherigen Position.

1. Warten Sie, bis TVSDK die `MediaPlayerEvent.SEEK_END` Callback.
1. Rufen Sie die endgültige angepasste Wiedergabeposition mithilfe des Positionsparameters des Rückrufs ab.

   Dies ist wichtig, da sich die tatsächliche Startposition nach der Suche von der angeforderten Position unterscheiden kann. Regeln, einschließlich des Wiedergabe-Verhaltens, werden ggf. angewendet, wenn eine Suche oder eine andere Neupositionierung mitten in einer Werbeunterbrechung endet oder Werbeunterbrechungen überspringt.

1. Verwenden Sie die Positionsinformationen, wenn Sie eine Suchleiste anzeigen.

<!--<a id="example_EEB73818260C43C8B5AE12BA68548AB7"></a>-->

**Suchbeispiel**

In diesem Beispiel scrubbt der Benutzer die Suchleiste, um an die gewünschte Position zu suchen.

```java
//Use the native SeekBar to set an OnSeekBarChangeListener to 
// see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) { 
            // Update the seek bar thumb with the position provided by the user. 
            setPosition(progress); 
        } 
    } 
 
    @Override 
    public void onStartTrackingTouch(SeekBar seekBar) { 
        isSeeking = true; 
    } 
 
    @Override 
    public void onStopTrackingTouch(SeekBar seekBar) { 
        isSeeking = false; 
 
        // Retrieve the playback range. 
        TimeRange playbackRange = mediaPlayer.getPlaybackRange(); 
 
        // Make sure to seek inside the playback range. 
        long seekPosition = Math.min(Math.round(seekBar.getProgress()), 
        playbackRange.getDuration()); 
     
        // Perform seek. 
        seek(playbackRange.getBegin() + seekPosition); 
    } 
}; 
```
