---
description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerStatus definiert.
title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '177'
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
