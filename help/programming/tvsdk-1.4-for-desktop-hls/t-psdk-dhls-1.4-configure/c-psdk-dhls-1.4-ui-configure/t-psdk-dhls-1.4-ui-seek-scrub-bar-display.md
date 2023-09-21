---
description: TVSDK unterstützt das Suchen nach einer bestimmten Position (Uhrzeit), an der der Stream eine gleitende Fensterwiedergabeliste ist, sowohl in Video On Demand (VOD) als auch in Live-Streams.
title: Anzeigen einer Suchscrubb-Leiste mit der aktuellen Wiedergabeposition
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Anzeigen einer Suchscrubb-Leiste mit der aktuellen Wiedergabeposition{#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK unterstützt das Suchen nach einer bestimmten Position (Uhrzeit), an der der Stream eine gleitende Fensterwiedergabeliste ist, sowohl in Video On Demand (VOD) als auch in Live-Streams.

>[!IMPORTANT]
>
>Die Suche in einem Live-Stream ist nur für DVR erlaubt.

1. Richten Sie Rückrufe für die Suche ein.

       Die Suche ist asynchron, sodass TVSDK die folgenden suchbezogenen Ereignisse sendet:
   
   * `SeekEvent.SEEK_BEGIN` - Suche starten.
   * `SeekEvent.SEEK_END` - Suche erfolgreich.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` - Die vom Benutzer angegebene Suchposition wurde angepasst.

1. Warten Sie, bis der Player einen gültigen Status für die Suche aufweist.

   Gültige Status sind VORBEREITT, ABGESCHLOSSEN, AUSGESETZT UND WIEDERGABE.

1. Suchen Sie nach dem entsprechenden Ereignis, um zu sehen, wann der Benutzer scrubbt.
1. Übergeben Sie die angeforderte Suchposition (Millisekunden) an die `MediaPlayer.seek` -Methode.

   ```
   function seek(position:Number):void;
   ```

   Sie können nur in der suchbaren Dauer des Assets suchen. Bei Video On Demand beträgt die Dauer zwischen 0 und der Dauer des Assets.

   >[!TIP]
   >
   >Dadurch wird der Abspielkopf an eine neue Position im Stream verschoben, die endgültige berechnete Position kann jedoch von der angegebenen Suchposition abweichen.

1. Warten Sie, bis TVSDK die `SeekEvent.SEEK_END` -Ereignis.
1. Rufen Sie die endgültige angepasste Wiedergabeposition mit event.ISTPosition ab.

       Dies ist wichtig, da sich die tatsächliche Startposition nach der Suche von der angeforderten Position unterscheiden kann. Es können verschiedene Regeln gelten, darunter:
   
   * Das Wiedergabe-Verhalten ist betroffen, wenn eine Suche oder eine andere Neupositionierung mitten in einer Werbeunterbrechung endet oder Werbeunterbrechungen überspringt.
   * Wenn Sie in der Nähe einer Segmentgrenze suchen, wird die Suchposition an den Anfang des Segments angepasst.

1. Verwenden Sie die Positionsinformationen, wenn Sie eine Suchleiste anzeigen.
