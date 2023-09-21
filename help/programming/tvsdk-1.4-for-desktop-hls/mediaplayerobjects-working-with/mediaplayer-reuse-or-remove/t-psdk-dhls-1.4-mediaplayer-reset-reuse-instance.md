---
description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie in den nicht initialisierten IDLE-Status zurückversetzt, wie in MediaPlayerStatus definiert.
title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz{#reset-or-reuse-a-mediaplayer-instance}

Sie können eine nicht mehr benötigte MediaPlayer-Instanz zurücksetzen, wiederverwenden oder freigeben.

Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie in den nicht initialisierten IDLE-Status zurückversetzt, wie in MediaPlayerStatus definiert.

Dieser Vorgang ist in den folgenden Fällen nützlich:

* Sie möchten eine `MediaPlayer` -Instanz, aber eine neue laden müssen `MediaResource` (Videoinhalt) und ersetzen Sie die vorherige Instanz.

  Durch Zurücksetzen können Sie die `MediaPlayer` -Instanz ohne den Mehraufwand für das Freigeben von Ressourcen, die `MediaPlayer`und die Neuzuweisung von Ressourcen. Die `replaceCurrentItem` und `replaceCurrentResource` -Methoden führen diese Schritte automatisch für Sie aus, ohne die Methode reset aufrufen zu müssen.

* Wenn die Variable `MediaPlayer` hat einen ERROR-Status und muss gelöscht werden.

  >[!IMPORTANT]
  >
  >Dies ist die einzige Möglichkeit, den ERROR-Status wiederherzustellen.

1. Aufruf `reset` , um `MediaPlayer` -Instanz in ihren nicht initialisierten Status zurück:

   ```
   function reset():void; 
   ```

1. Verwendung `MediaPlayer.replaceCurrentItem` oder `MediaPlayer.replaceCurrentResource` Laden eines anderen `MediaResource`.

   >[!TIP]
   >
   >Um einen Fehler zu löschen, müssen Sie denselben `MediaResource`.

1. Wenn Sie die `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` mit dem `PREPARED` -Status, starten Sie die Wiedergabe.
