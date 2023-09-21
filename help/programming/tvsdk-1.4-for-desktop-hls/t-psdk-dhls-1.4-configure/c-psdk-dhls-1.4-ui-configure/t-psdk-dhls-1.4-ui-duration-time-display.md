---
description: Sie können TVSDK verwenden, um Informationen zu den Medien abzurufen, die Sie in der Suchleiste anzeigen können.
title: Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen{#display-the-duration-current-time-and-remaining-time-of-the-video}

Sie können TVSDK verwenden, um Informationen zu den Medien abzurufen, die Sie in der Suchleiste anzeigen können.

1. Warten Sie, bis Ihr Player den Status INITIALISIERT aufweist.
1. Rufen Sie die aktuelle Abspielleistenzeit mit dem `MediaPlayer.currentTime` -Eigenschaft.

   Dadurch wird die aktuelle Abspielposition auf der virtuellen Timeline in Millisekunden zurückgegeben. Die Zeit wird relativ zum aufgelösten Stream berechnet, der möglicherweise mehrere Instanzen von alternativen Inhalten enthält, z. B. mehrere Anzeigen oder Werbeunterbrechungen, die in den Haupt-Stream aufgeteilt sind. Bei Live-/linearen Streams befindet sich die zurückgegebene Zeit immer im Bereich des Wiedergabefensters.

   ```
   function get currentTime():Number;
   ```

1. Rufen Sie den Wiedergabebereich des Streams ab und bestimmen Sie die Dauer.
   1. Verwenden Sie die `mediaPlayer.playbackRange` -Eigenschaft, um den virtuellen Zeitbereich der Zeitleiste abzurufen.

      ```
      function get playbackRange():TimeRange;
      ```

   1. Analysieren des Zeitraums mit `mediacore.utils.TimeRange`.
   1. Um die Dauer zu bestimmen, subtrahieren Sie den Start vom Ende des Bereichs.

      Dies umfasst die Dauer von zusätzlichem Inhalt, der in den Stream (Anzeigen) eingefügt wird.

      Bei VOD beginnt der Bereich immer mit null und der Endwert entspricht der Summe der Dauer des Hauptinhalts und der Dauer des zusätzlichen Inhalts, der in den Stream (Anzeigen) eingefügt wird.

      Bei einem linearen/Live-Asset stellt der Bereich den Bereich des Wiedergabefensters dar und dieser Bereich ändert sich während der Wiedergabe.

      TVSDK sendet eine `MediaPlayerItemEvent.ITEM_UPDATED` -Ereignis, um anzugeben, dass das Medienelement aktualisiert wurde und seine Attribute (einschließlich des Wiedergabebereichs) aktualisiert wurden.

1. Verwenden Sie die verfügbaren Methoden für die `MediaPlayer` und `HSlider` -Klasse, die im Flex SDK öffentlich verfügbar ist, um die Suchleistenparameter einzurichten.

1. Verwenden Sie einen Timer, um die aktuelle Zeit regelmäßig abzurufen und die `SeekBar`.
