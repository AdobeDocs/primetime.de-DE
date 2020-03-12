---
description: Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie MediaResource nicht mehr benötigen.
seo-description: Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie MediaResource nicht mehr benötigen.
seo-title: Eine MediaPlayer-Instanz und Ressourcen freigeben
title: Eine MediaPlayer-Instanz und Ressourcen freigeben
uuid: e7b2112e-8add-4789-9345-5f829d39d639
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Eine MediaPlayer-Instanz und Ressourcen freigeben{#release-a-mediaplayer-instance-and-resources}

Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie MediaResource nicht mehr benötigen.

Wenn Sie ein `MediaPlayer` Objekt freigeben, werden die mit diesem `MediaPlayer` Objekt verknüpften zugrunde liegenden Hardware-Ressourcen entzogen.

Es gibt einige Gründe für die Veröffentlichung eines `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann sich auf die Leistung auswirken.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es zu einem Wiedergabefehler für andere Anwendungen kommen.

1. Lassen Sie die `MediaPlayer`Lösung frei.

   ```
   function release():void;
   ```

Nachdem die `MediaPlayer` Instanz freigegeben wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` Schnittstelle nach der Freigabe aufgerufen wird, wird eine `IllegalStateException` ausgelöst.