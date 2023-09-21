---
description: Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie die MediaResource nicht mehr benötigen.
title: MediaPlayer-Instanz und -Ressourcen freigeben
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# MediaPlayer-Instanz und -Ressourcen freigeben{#release-a-mediaplayer-instance-and-resources}

Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie die MediaResource nicht mehr benötigen.

Wenn Sie eine `MediaPlayer` -Objekt, die zugrunde liegenden Hardware-Ressourcen, die damit verknüpft sind `MediaPlayer` -Objekt zugewiesen wird.

Im Folgenden finden Sie einige Gründe für die Veröffentlichung einer `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann die Leistung beeinträchtigen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es bei anderen Anwendungen zu Wiedergabefehlern kommen.

1. Lassen Sie die `MediaPlayer`.

   ```
   function release():void;
   ```

Nach dem `MediaPlayer` -Instanz veröffentlicht wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` -Schnittstelle aufgerufen wird, nachdem sie veröffentlicht wurde, wird ein `IllegalStateException` geworfen wird.
