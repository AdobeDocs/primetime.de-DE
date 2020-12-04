---
description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerStatus definiert.
seo-description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerStatus definiert.
seo-title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
uuid: b376096b-0aed-4ac2-96e5-e30a4eaf742e
translation-type: tm+mt
source-git-commit: c547002eb8946f8ccc5a79d0836f3f814e823b97
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz{#reset-or-reuse-a-mediaplayer-instance}

Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.

Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerStatus definiert.

Dieser Vorgang ist in den folgenden Fällen nützlich:

* Sie möchten eine `MediaPlayer`-Instanz wiederverwenden, müssen jedoch eine neue `MediaResource` (Videoinhalt) laden und die vorherige Instanz ersetzen.

   Durch Zurücksetzen können Sie die `MediaPlayer`-Instanz wiederverwenden, ohne den Aufwand für die Freigabe von Ressourcen, das Neuerstellen der `MediaPlayer`-Instanz und das Neuzuordnen von Ressourcen zu verursachen. Die Methoden `replaceCurrentItem` und `replaceCurrentResource` führen diese Schritte automatisch für Sie aus, ohne die Methode reset aufrufen zu müssen.

* Wenn das `MediaPlayer` einen ERROR-Status hat und gelöscht werden muss.

   >[!IMPORTANT]
   >
   >Dies ist die einzige Möglichkeit, um sich vom ERROR-Status zu erholen.

1. Rufen Sie `reset` auf, um die `MediaPlayer`-Instanz in ihren nicht initialisierten Status zurückzugeben:

   ```
   function reset():void; 
   ```

1. Verwenden Sie `MediaPlayer.replaceCurrentItem` oder `MediaPlayer.replaceCurrentResource`, um ein anderes `MediaResource` zu laden.

   >[!TIP]
   >
   >Um einen Fehler zu löschen, laden Sie dasselbe `MediaResource`.

1. Wenn Sie das `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` mit dem Status `PREPARED` erhalten, wird die Wiedergabe Beginn.
