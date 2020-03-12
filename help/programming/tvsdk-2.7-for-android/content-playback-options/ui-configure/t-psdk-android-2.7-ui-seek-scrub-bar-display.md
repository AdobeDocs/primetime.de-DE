---
description: TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window Playlist ist, in Video on Demand (VOD) und Live Streams.
seo-description: TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window Playlist ist, in Video on Demand (VOD) und Live Streams.
seo-title: Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition
title: Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition
uuid: df045a10-8d74-4874-8fa5-7e9571c8678d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window Playlist ist, in Video on Demand (VOD) und Live Streams.

>[!TIP]
>
>Die Suche in einem Live-Stream ist nur für DVR zulässig.

1. Richten Sie Rückrufe für die Suche ein.

       Die Suche erfolgt asynchron, sodass TVSDK die folgenden suchbezogenen Ereignis auslöst:
   
   * `MediaPlayerEvent.SEEK_BEGIN`, wobei die Suche Beginn.
   * `MediaPlayerEvent.SEEK_END`, wobei die Suche erfolgreich ist.
   * `MediaPlayerEvent.OPERATION_FAILED`, wo die Suche fehlgeschlagen ist.

1. Warten Sie, bis der Player einen gültigen Status für die Suche hat.

   Die gültigen Status sind VORBEREITT, ABGESCHLOSSEN, ANGEHALTEN UND WIEDERGABE.
1. Verwenden Sie den nativen `SeekBar` zur Einstellung, `OnSeekBarChangeListener`der festlegt, wann der Benutzer scrubbt.
1. Übergeben Sie die angeforderte Suchposition (Millisekunden) an die `MediaPlayer.seek` Methode.

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   Sie können nur in der suchbaren Dauer des Assets suchen. Bei Videos bei Bedarf, d. h. zwischen 0 und der Dauer des Assets.

   >[!TIP]
   >
   >Durch diesen Schritt wird der Abspielkopf an eine neue Position im Stream verschoben, aber die finale berechnete Position kann sich von der angegebenen Suchposition unterscheiden.

1. Suchen Sie nach geeigneten Maßnahmen `MediaPlayerEvent.OPERATION_FAILED` und ergreifen Sie entsprechende Maßnahmen.

   Dieses Ereignis gibt die entsprechende Warnung aus. Ihre Anwendung legt fest, wie Sie fortfahren. Zu den Optionen gehören der erneute Versuch der Suche oder die Fortsetzung der Wiedergabe von der vorherigen Position.

1. Warten Sie, bis TVSDK den `MediaPlayerEvent.SEEK_END` Rückruf aufruft.
1. Rufen Sie die endgültige angepasste Abspielposition mit dem Parameter position des Callbacks ab.

   Dies ist wichtig, da sich die tatsächliche Position des Beginns nach der Suche von der angeforderten Position unterscheiden kann. Regeln, einschließlich des Wiedergabeverhaltens, sind betroffen, wenn eine Suche oder eine andere Neupositionierung mitten in einer Werbeunterbrechung endet oder Werbeunterbrechungen übersprungen werden.

1. Verwenden Sie die Positionsinformationen, wenn Sie eine Suchabfrageleiste anzeigen.

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

