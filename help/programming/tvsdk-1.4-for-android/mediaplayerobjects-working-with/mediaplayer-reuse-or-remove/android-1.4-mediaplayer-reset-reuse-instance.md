---
description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie in den nicht initialisierten IDLE-Status zurückversetzt, wie in MediaPlayerState definiert.
title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Zurücksetzen, Wiederverwenden oder Entfernen einer MediaPlayer-Instanz {#reset-or-reuse-a-mediaplayer-instance}

Sie können eine nicht mehr benötigte MediaPlayer-Instanz zurücksetzen, wiederverwenden oder freigeben.

Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie in den nicht initialisierten IDLE-Status zurückversetzt, wie in MediaPlayerState definiert.

Dieser Vorgang ist in den folgenden Fällen nützlich:

* Sie möchten eine `MediaPlayer` -Instanz, aber eine neue laden müssen `MediaResource` (Videoinhalt) und ersetzen Sie die vorherige Instanz.

  Durch Zurücksetzen können Sie die `MediaPlayer` -Instanz ohne den Mehraufwand für das Freigeben von Ressourcen, die `MediaPlayer`und die Neuzuweisung von Ressourcen.

* Wenn die Variable `MediaPlayer` hat einen ERROR-Status und muss gelöscht werden.

  >[!IMPORTANT]
  >
  >Dies ist die einzige Möglichkeit, den FEHLER-Status wiederherzustellen.

1. Aufruf `reset` , um `MediaPlayer` -Instanz in ihren nicht initialisierten Status zurück:

   ```java
   void reset() throws IllegalStateException; 
   ```

1. Verwendung `MediaPlayer.replaceCurrentResource` Laden eines anderen `MediaResource`.

   >[!TIP]
   >
   >Um einen Fehler zu löschen, müssen Sie denselben `MediaResource`.

1. Wenn Sie die `STATUS_CHANGED` Ereignisrückruf mit VORBEREITTEM Status, die Wiedergabe starten.

## MediaPlayer-Instanz und -Ressourcen freigeben{#release-a-mediaplayer-instance-and-resources}

Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie die MediaResource nicht mehr benötigen.

Wenn Sie eine `MediaPlayer` -Objekt, die zugrunde liegenden Hardware-Ressourcen, die damit verknüpft sind `MediaPlayer` -Objekt zugewiesen wird.

Im Folgenden finden Sie einige Gründe für die Veröffentlichung eines MediaPlayers:

* Das Halten unnötiger Ressourcen kann die Leistung beeinträchtigen.
* Unnötig machen `MediaPlayer` -Objekt kann zu einem kontinuierlichen Akkuverbrauch für Mobilgeräte führen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es bei anderen Anwendungen zu Wiedergabefehlern kommen.

1. Lassen Sie die `MediaPlayer`.

   ```java
   void release() throws IllegalStateException;
   ```

Nach dem `MediaPlayer` -Instanz veröffentlicht wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` -Schnittstelle aufgerufen wird, nachdem sie veröffentlicht wurde, wird ein `IllegalStateException` geworfen wird.
