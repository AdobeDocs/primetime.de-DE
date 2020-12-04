---
description: TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window-Playlist ist, sowohl in Video on Demand (VOD) als auch in Live-Streams.
seo-description: TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window-Playlist ist, sowohl in Video on Demand (VOD) als auch in Live-Streams.
seo-title: Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition
title: Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition
uuid: a9f4dd6c-78cf-455c-8c31-b2f7b740d84a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window-Playlist ist, sowohl in Video on Demand (VOD) als auch in Live-Streams.

>[!IMPORTANT]
>
>Die Suche in einem Live-Stream ist nur für DVR zulässig.

1. Richten Sie Rückrufe für die Suche ein.

       Die Suche erfolgt asynchron, sodass TVSDK die folgenden suchbezogenen Ereignis auslöst:
   
   * `QOSEventListener.onSeekStart` - Suche beginnt.
   * `QOSEventListener.onSeekComplete` - Suche erfolgreich.
   * `QOSEventListener.onOperationFailed` - Suche fehlgeschlagen.

1. Warten Sie, bis der Player einen gültigen Status für die Suche aufweist.

   Gültige Status sind &quot;VORBEREITEN&quot;, &quot;ABGESCHLOSSEN&quot;, &quot;ANGEHALTEN&quot;und &quot;WIEDERGABE&quot;.

1. Verwenden Sie die native SeekBar, um `OnSeekBarChangeListener` einzustellen, um zu sehen, wann der Benutzer scrubbt.
1. Suchen Sie nach `QOSEventListener.onOperationFailed` und gehen Sie entsprechend vor.

   Dieses Ereignis gibt die entsprechende Warnung aus. Ihre Anwendung legt fest, wie Sie zum Beispiel fortfahren, indem Sie die Suche erneut ausführen oder die Wiedergabe von der vorherigen Position fortsetzen.

1. Warten Sie, bis TVSDK den Rückruf `QOSEventListener.onSeekComplete` aufruft.
1. Rufen Sie die endgültige angepasste Abspielposition mit dem Parameter position des Callbacks ab.

   Dies ist wichtig, da sich die tatsächliche Position des Beginns nach der Suche von der angeforderten Position unterscheiden kann. Das Wiedergabeverhalten kann beeinträchtigt werden, wenn eine Suche oder eine andere Neupositionierung mitten in einer Werbeunterbrechung endet oder Werbeunterbrechungen übersprungen werden.

1. Verwenden Sie die Positionsinformationen, wenn Sie eine Suchabfrageleiste anzeigen.

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

