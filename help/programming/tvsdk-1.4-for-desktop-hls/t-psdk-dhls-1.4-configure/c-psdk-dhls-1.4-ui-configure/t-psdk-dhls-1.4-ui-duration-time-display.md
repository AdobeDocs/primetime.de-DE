---
description: Sie können TVSDK verwenden, um Informationen über die Medien abzurufen, die Sie in der Suchleiste anzeigen können.
seo-description: Sie können TVSDK verwenden, um Informationen über die Medien abzurufen, die Sie in der Suchleiste anzeigen können.
seo-title: Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen
title: Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen
uuid: 64536ba7-33a1-49f8-a947-5700e1e9c032
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Dauer, aktuelle Zeit und verbleibende Zeit des Videos anzeigen{#display-the-duration-current-time-and-remaining-time-of-the-video}

Sie können TVSDK verwenden, um Informationen über die Medien abzurufen, die Sie in der Suchleiste anzeigen können.

1. Warten Sie, bis Ihr Spieler den Status INITIALIZED hat.
1. Rufen Sie die aktuelle Abspielposition mit der `MediaPlayer.currentTime` Eigenschaft ab.

   Dadurch wird die aktuelle Abspielposition auf der virtuellen Zeitleiste in Millisekunden zurückgegeben. Die Zeit wird relativ zum aufgelösten Stream berechnet, der mehrere Instanzen alternativen Inhalts enthalten kann, z. B. mehrere Anzeigen oder Werbeunterbrechungen, die in den Hauptstrom kopiert werden. Bei Live-/linearen Streams liegt die zurückgegebene Zeit immer im Bereich des Wiedergabefensters.

   ```
   function get currentTime():Number;
   ```

1. Rufen Sie den Wiedergabebereich des Streams ab und bestimmen Sie die Dauer.
   1. Verwenden Sie die `mediaPlayer.playbackRange` Eigenschaft, um den virtuellen Zeitleistenzeitbereich abzurufen.

      ```
      function get playbackRange():TimeRange;
      ```

   1. Analysieren Sie den Zeitraum mit `mediacore.utils.TimeRange`.
   1. Um die Dauer zu bestimmen, ziehen Sie den Beginn vom Ende des Bereichs ab.

      Dies umfasst die Dauer zusätzlicher Inhalte, die in den Stream (Anzeigen) eingefügt werden.

      Bei VOD beginnt der Bereich immer mit null und der Endwert entspricht der Summe der Dauer des Hauptinhalts und der Dauer des zusätzlichen Inhalts, der in den Stream eingefügt wird (Anzeigen).

      Bei einem linearen/Live-Asset steht der Bereich für den Bereich des Wiedergabefensters, und dieser Bereich ändert sich während der Wiedergabe.

      TVSDK sendet ein `MediaPlayerItemEvent.ITEM_UPDATED` Ereignis, um anzugeben, dass das Medienelement aktualisiert wurde und seine Attribute (einschließlich des Wiedergabebereichs) aktualisiert wurden.

1. Verwenden Sie die im Flex SDK verfügbaren Methoden für die `MediaPlayer` und die `HSlider` Klasse, die öffentlich verfügbar sind, um die Suchleistenparameter einzurichten.

1. Verwenden Sie einen Timer, um in regelmäßigen Abständen die aktuelle Zeit abzurufen und die `SeekBar`zu aktualisieren.
