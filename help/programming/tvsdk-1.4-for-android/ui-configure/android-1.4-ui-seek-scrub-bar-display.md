---
description: TVSDK unterstützt das Suchen nach einer bestimmten Position (Uhrzeit), an der der Stream eine gleitende Fensterwiedergabeliste ist, sowohl in Video On Demand (VOD) als auch in Live-Streams.
title: Anzeigen einer Suchscrubb-Leiste mit der aktuellen Wiedergabeposition
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Anzeigen einer Suchscrubb-Leiste mit der aktuellen Wiedergabeposition {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK unterstützt das Suchen nach einer bestimmten Position (Uhrzeit), an der der Stream eine gleitende Fensterwiedergabeliste ist, sowohl in Video On Demand (VOD) als auch in Live-Streams.

>[!IMPORTANT]
>
>Die Suche in einem Live-Stream ist nur für DVR erlaubt.

1. Richten Sie Rückrufe für die Suche ein.

       Die Suche ist asynchron, sodass TVSDK die folgenden suchbezogenen Ereignisse sendet:
   
   * `QOSEventListener.onSeekStart` - Suche starten.
   * `QOSEventListener.onSeekComplete` - Suche erfolgreich.
   * `QOSEventListener.onOperationFailed` - Suche fehlgeschlagen.

1. Warten Sie, bis der Player für die Suche einen gültigen Status aufweist.

   Gültige Status sind PREPARED, COMPLETE, PAUSED und PLAYING.

1. Verwenden Sie die native SeekBar, um `OnSeekBarChangeListener` , um zu sehen, wann der Benutzer scrubbt.
1. Suchen Sie nach `QOSEventListener.onOperationFailed` und geeignete Maßnahmen ergreifen.

   Dieses Ereignis übergibt die entsprechende Warnung. Ihre Anwendung bestimmt beispielsweise, wie Sie fortfahren, indem Sie die Suche erneut durchführen oder die Wiedergabe von der vorherigen Position fortsetzen.

1. Warten Sie, bis TVSDK die `QOSEventListener.onSeekComplete` Callback.
1. Rufen Sie die endgültige angepasste Wiedergabeposition mithilfe des Positionsparameters des Rückrufs ab.

   Dies ist wichtig, da sich die tatsächliche Startposition nach der Suche von der angeforderten Position unterscheiden kann. Das Wiedergabe-Verhalten kann beeinträchtigt werden, wenn eine Suche oder eine andere Neupositionierung mitten in einer Werbeunterbrechung endet oder die Anzeige abgebrochen wird.

1. Verwenden Sie die Positionsinformationen, wenn Sie eine Suchleiste anzeigen.

<!--<a id="example_9657AA855B6A4355B0E7D854596FFB54"></a>-->

**Suchbeispiel**

In diesem Beispiel scrubbt der Benutzer die Suchleiste, um an die gewünschte Position zu suchen.

```java
// Use the native SeekBar to set OnSeekBarChangeListener to  
//see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) {  
            // Update the seek bar thumb, with the position provided by the user. 
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
