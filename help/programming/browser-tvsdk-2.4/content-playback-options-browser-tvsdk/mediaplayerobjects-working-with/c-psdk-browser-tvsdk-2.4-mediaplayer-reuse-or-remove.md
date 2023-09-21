---
description: Sie können eine nicht mehr benötigte MediaPlayer-Instanz zurücksetzen, wiederverwenden oder freigeben.
title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Wiederverwenden oder Entfernen einer MediaPlayer-Instanz{#reuse-or-remove-a-mediaplayer-instance}

Sie können eine nicht mehr benötigte MediaPlayer-Instanz zurücksetzen, wiederverwenden oder freigeben.

## Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz {#section_C183E6164C184C3CBC5321FC6A2528EA}

Sie können eine `MediaPlayer` -Instanz, um sie in den nicht initialisierten IDLE-Status zurückzuversetzen, wie in `MediaPlayerStatus`. Sie können auch das aktuelle Medienelement ersetzen oder mit einer zuvor geladenen Medienressource ein neues festlegen.

Dieser Vorgang ist in den folgenden Fällen nützlich:

* Sie möchten eine `MediaPlayer` -Instanz, aber eine neue laden müssen `MediaResource` (Videoinhalt) und ersetzen Sie die vorherige Instanz.

  Durch Zurücksetzen können Sie die `MediaPlayer` -Instanz ohne den Mehraufwand für das Freigeben von Ressourcen, die `MediaPlayer`und die Neuzuweisung von Ressourcen. Die `replaceCurrentItem` -Methode führt diese Schritte automatisch für Sie aus.

* Wenn die Variable `MediaPlayer` hat einen ERROR-Status und muss gelöscht werden.

  >[!IMPORTANT]
  >
  >Dies ist die einzige Möglichkeit, den FEHLER-Status wiederherzustellen.

1. Aufruf `MediaPlayer.reset()` , um `MediaPlayer` -Instanz in ihren nicht initialisierten Status zurück:

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Aufruf `MediaPlayer.replaceCurrentItem()` Laden eines anderen `MediaResource`

   >[!TIP]
   >
   >Um einen Fehler zu löschen, müssen Sie denselben `MediaResource`.

1. Rufen Sie die `prepareToPlay()` -Methode.

   >[!NOTE]
   >
   >Wenn Sie die `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` -Ereignis mit dem Status VORBEREITET festlegen, können Sie die Wiedergabe starten.

## MediaPlayer-Instanz und -Ressourcen freigeben {#section_2D159975C82245098E7078FE0B1578CE}

Sie sollten eine `MediaPlayer` Instanz und Ressourcen, wenn Sie die MediaResource nicht mehr benötigen.

Im Folgenden finden Sie einige Gründe für die Veröffentlichung einer `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann die Leistung beeinträchtigen.
* Unnötig machen `MediaPlayer` -Objekt kann zu einem kontinuierlichen Akkuverbrauch für Mobilgeräte führen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es bei anderen Anwendungen zu Wiedergabefehlern kommen.

* Lassen Sie die `MediaPlayer`.

  ```js
  void release()
  ```

  >[!NOTE]
  >
  >Nach dem `MediaPlayer` -Instanz veröffentlicht wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` -Schnittstelle aufgerufen wird, nachdem sie veröffentlicht wurde, wird ein `IllegalStateException` geworfen wird.
