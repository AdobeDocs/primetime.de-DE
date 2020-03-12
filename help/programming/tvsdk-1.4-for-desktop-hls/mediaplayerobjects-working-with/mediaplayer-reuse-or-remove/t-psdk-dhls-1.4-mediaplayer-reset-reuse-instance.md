---
description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerStatus definiert.
seo-description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerStatus definiert.
seo-title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
uuid: b376096b-0aed-4ac2-96e5-e30a4eaf742e
translation-type: tm+mt
source-git-commit: c547002eb8946f8ccc5a79d0836f3f814e823b97

---


# Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz{#reset-or-reuse-a-mediaplayer-instance}

Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.

Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerStatus definiert.

Dieser Vorgang ist in den folgenden Fällen nützlich:

* Sie möchten eine `MediaPlayer` Instanz wiederverwenden, müssen jedoch eine neue Instanz laden `MediaResource` (Videoinhalt) und die vorherige Instanz ersetzen.

   Durch Zurücksetzen können Sie die `MediaPlayer` Instanz wiederverwenden, ohne dass die Freigabe von Ressourcen, die Wiederherstellung der Ressourcen `MediaPlayer`und die Neuzuweisung von Ressourcen mit Aufwand verbunden ist. Die `replaceCurrentItem` und `replaceCurrentResource` -Methoden führen diese Schritte automatisch für Sie aus, ohne die Methode reset aufrufen zu müssen.

* Wenn der `MediaPlayer` Status FEHLER aufweist und gelöscht werden muss.

   >[!IMPORTANT]
   >
   >Dies ist die einzige Möglichkeit, um sich vom ERROR-Status zu erholen.

1. Aufruf `reset` zur Wiederherstellung des `MediaPlayer` nicht initialisierten Status:

   ```
   function reset():void; 
   ```

1. Verwenden Sie `MediaPlayer.replaceCurrentItem` oder `MediaPlayer.replaceCurrentResource` , um eine andere zu laden `MediaResource`.

   >[!TIP]
   >
   >Um einen Fehler zu löschen, müssen Sie dasselbe laden `MediaResource`.

1. Wenn Sie den `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` Status &quot; `PREPARED` status&quot;erhalten, wird die Wiedergabe Beginn.
