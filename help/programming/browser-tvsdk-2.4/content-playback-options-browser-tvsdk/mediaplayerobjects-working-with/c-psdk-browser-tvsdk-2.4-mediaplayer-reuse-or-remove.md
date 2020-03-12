---
description: Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.
seo-description: Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.
seo-title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
uuid: 0b9a06b0-ece7-4e18-9221-a4528bcbc141
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Wiederverwenden oder Entfernen einer MediaPlayer-Instanz{#reuse-or-remove-a-mediaplayer-instance}

Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.

## Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz {#section_C183E6164C184C3CBC5321FC6A2528EA}

Sie können eine `MediaPlayer` Instanz zurücksetzen, um sie wieder in ihren nicht initialisierten IDLE-Status zurückzusetzen, wie in `MediaPlayerStatus`. Sie können auch das aktuelle Medienelement ersetzen oder ein neues mithilfe einer zuvor geladenen Medienressource festlegen.

Dieser Vorgang ist in den folgenden Fällen nützlich:

* Sie möchten eine `MediaPlayer` Instanz wiederverwenden, müssen jedoch eine neue Instanz laden `MediaResource` (Videoinhalt) und die vorherige Instanz ersetzen.

   Durch Zurücksetzen können Sie die `MediaPlayer` Instanz wiederverwenden, ohne dass die Freigabe von Ressourcen, die Wiederherstellung der Ressourcen `MediaPlayer`und die Neuzuweisung von Ressourcen mit Aufwand verbunden ist. Die `replaceCurrentItem` Methode führt diese Schritte automatisch für Sie aus.

* Wenn der `MediaPlayer` Status FEHLER ist und gelöscht werden muss.

   >[!IMPORTANT]
   >
   >Dies ist die einzige Möglichkeit, sich vom FEHLER-Zustand zu erholen.

1. Aufruf `MediaPlayer.reset()` zur Wiederherstellung des `MediaPlayer` nicht initialisierten Status:

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Aufruf `MediaPlayer.replaceCurrentItem()` zum Laden eines weiteren `MediaResource`

   >[!TIP]
   >
   >Um einen Fehler zu löschen, müssen Sie dasselbe laden `MediaResource`.

1. Rufen Sie die `prepareToPlay()` Methode auf.

   >[!NOTE]
   >
   >Wenn Sie das `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` Ereignis mit dem Status &quot;VORBEREITT&quot;erhalten, können Sie die Wiedergabe Beginn haben.

## Eine MediaPlayer-Instanz und Ressourcen freigeben {#section_2D159975C82245098E7078FE0B1578CE}

Sie sollten eine `MediaPlayer` Instanz und Ressourcen freigeben, wenn Sie MediaResource nicht mehr benötigen.

Es gibt einige Gründe für die Veröffentlichung eines `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann sich auf die Leistung auswirken.
* Das Verlassen eines unnötigen `MediaPlayer` Objekts kann zu einem kontinuierlichen Akkuverbrauch von Mobilgeräten führen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es zu einem Wiedergabefehler für andere Anwendungen kommen.

* Lassen Sie die `MediaPlayer`Lösung frei.

   ```js
   void release()
   ```

   >[!NOTE]
   >
   >Nachdem die `MediaPlayer` Instanz freigegeben wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` Schnittstelle nach der Freigabe aufgerufen wird, wird eine `IllegalStateException` ausgelöst.

