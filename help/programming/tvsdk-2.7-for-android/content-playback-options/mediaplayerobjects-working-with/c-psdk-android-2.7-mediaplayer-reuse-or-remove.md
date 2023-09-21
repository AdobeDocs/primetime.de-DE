---
description: Sie können eine nicht mehr benötigte MediaPlayer-Instanz zurücksetzen, wiederverwenden oder freigeben.
title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Wiederverwenden oder Entfernen einer MediaPlayer-Instanz {#reuse-or-remove-a-mediaplayer-instance}

Sie können eine nicht mehr benötigte MediaPlayer-Instanz zurücksetzen, wiederverwenden oder freigeben.

## Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Wenn Sie eine `MediaPlayer` -Instanz wird sie in den nicht initialisierten IDLE-Status zurückversetzt, wie in `MediaPlayerStatus`

* Sie möchten eine `MediaPlayer` -Instanz, aber eine neue laden müssen `MediaResource` (Videoinhalt) und ersetzen Sie die vorherige Instanz.

  Durch Zurücksetzen können Sie die `MediaPlayer` -Instanz ohne den Mehraufwand für das Freigeben von Ressourcen, die `MediaPlayer`und die Neuzuweisung von Ressourcen.

* Wenn die Variable `MediaPlayer` hat den ERROR-Status und muss gelöscht werden.

  >[!IMPORTANT]
  >
  >Dies ist die einzige Möglichkeit, den ERROR-Status wiederherzustellen.

   1. Aufruf `reset` , um `MediaPlayer` -Instanz auf ihren nicht initialisierten Status zurück:

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Verwendung `MediaPlayer.replaceCurrentResource()` Laden eines anderen `MediaResource`.

      >[!NOTE]
      >
      >Um einen Fehler zu löschen, müssen Sie denselben `MediaResource`.

   1. Wenn Sie die `STATUS_CHANGED` Ereignis-Callback mit `PREPARED` -Status, starten Sie die Wiedergabe.

## MediaPlayer-Instanz und -Ressourcen freigeben {#section_13A0914AFF784943ABC343F7EB249C4E}

Sie sollten eine `MediaPlayer` Instanz und Ressourcen, wenn Sie die `MediaResource`.

Wenn Sie eine `MediaPlayer` -Objekt, die zugrunde liegenden Hardware-Ressourcen, die damit verknüpft sind `MediaPlayer` -Objekt zugewiesen wird.

Im Folgenden finden Sie einige Gründe für die Veröffentlichung einer `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann die Leistung beeinträchtigen.
* Unnötig machen `MediaPlayer` -Objekt instanziiert kann zu einem kontinuierlichen Akkuverbrauch für Mobilgeräte führen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es bei anderen Anwendungen zu Wiedergabefehlern kommen.

* Lassen Sie die `MediaPlayer`.

  ```java
  void release() throws MediaPlayerException;
  ```

  >[!NOTE]
  >
  >Nach dem `MediaPlayer` -Instanz veröffentlicht wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` -Schnittstelle aufgerufen wird, nachdem sie veröffentlicht wurde, wird ein `MediaPlayerException` geworfen wird.
