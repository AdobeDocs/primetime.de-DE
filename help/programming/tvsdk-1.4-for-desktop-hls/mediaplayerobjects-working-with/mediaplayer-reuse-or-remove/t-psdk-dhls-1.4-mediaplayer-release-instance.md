---
description: Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie MediaResource nicht mehr benötigen.
title: Eine MediaPlayer-Instanz und Ressourcen freigeben
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---


# MediaPlayer-Instanz und -Ressourcen freigeben{#release-a-mediaplayer-instance-and-resources}

Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie MediaResource nicht mehr benötigen.

Wenn Sie ein `MediaPlayer`-Objekt freigeben, werden die zugrunde liegenden Hardwareressourcen, die mit diesem `MediaPlayer`-Objekt verknüpft sind, dezugeordnet.

Es gibt einige Gründe für die Veröffentlichung eines `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann sich auf die Leistung auswirken.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es zu einem Wiedergabefehler für andere Anwendungen kommen.

1. Lassen Sie `MediaPlayer` los.

   ```
   function release():void;
   ```

Nachdem die `MediaPlayer`-Instanz freigegeben wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer`-Schnittstelle nach der Veröffentlichung aufgerufen wird, wird ein `IllegalStateException`-Ereignis ausgelöst.