---
description: TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window-Playlist ist, sowohl in Video on Demand (VOD) als auch in Live-Streams.
seo-description: TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window-Playlist ist, sowohl in Video on Demand (VOD) als auch in Live-Streams.
seo-title: Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition
title: Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition
uuid: f940b305-4893-4531-9a79-53670f5fd23f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition{#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK unterstützt die Suche nach einer bestimmten Position (Zeit), an der der Stream eine Sliding-Window-Playlist ist, sowohl in Video on Demand (VOD) als auch in Live-Streams.

>[!IMPORTANT]
>
>Die Suche in einem Live-Stream ist nur für DVR zulässig.

1. Richten Sie Rückrufe für die Suche ein.

       Die Suche erfolgt asynchron, sodass TVSDK die folgenden suchbezogenen Ereignis auslöst:
   
   * `SeekEvent.SEEK_BEGIN` - Suche beginnt.
   * `SeekEvent.SEEK_END` - Suche erfolgreich.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` - Die vom Benutzer angegebene Suchposition wurde angepasst.

1. Warten Sie, bis der Player einen gültigen Status für die Suche hat.

   Gültige Status sind &quot;VORBEREITEN&quot;, &quot;ABGESCHLOSSEN&quot;, &quot;AUSGEHALTEN&quot;und &quot;WIEDERGABE&quot;.

1. Suchen Sie nach dem entsprechenden Ereignis, um zu sehen, wann der Benutzer mit dem Scrubbing beginnt.
1. Übergeben Sie die angeforderte Suchposition (Millisekunden) an die `MediaPlayer.seek`-Methode.

   ```
   function seek(position:Number):void;
   ```

   Sie können nur in der suchbaren Dauer des Assets suchen. Bei Video-on-Demand dauert die Dauer zwischen 0 und der Dauer des Assets.

   >[!TIP]
   >
   >Dadurch wird der Abspielkopf an eine neue Position im Stream verschoben, aber die finale berechnete Position kann sich von der angegebenen Suchposition unterscheiden.

1. Warten Sie, bis TVSDK das `SeekEvent.SEEK_END`-Ereignis auslöst.
1. Rufen Sie die endgültige angepasste Abspielposition mit Ereignis.ISTPosition ab.

       Dies ist wichtig, da sich die tatsächliche Position des Beginns nach der Suche von der angeforderten Position unterscheiden kann. Es können verschiedene Regeln gelten, darunter:
   
   * Das Wiedergabeverhalten wirkt sich darauf aus, wenn eine Suche oder eine andere Neupositionierung mitten in einer Werbeunterbrechung endet oder Werbeunterbrechungen übersprungen werden.
   * Wenn Sie in der Nähe einer Segmentgrenze suchen, wird die Suchposition an den Anfang des Segments angepasst.

1. Verwenden Sie die Positionsinformationen, wenn Sie eine Suchabfrageleiste anzeigen.
