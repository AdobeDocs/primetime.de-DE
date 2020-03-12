---
description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerState definiert.
seo-description: Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerState definiert.
seo-title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
title: Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz
uuid: 72cc4511-8ab0-44e5-b93c-b36f0321bba8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Zurücksetzen, Wiederverwenden oder Entfernen einer MediaPlayer-Instanz {#reset-or-reuse-a-mediaplayer-instance}

Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.

Wenn Sie eine MediaPlayer-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in MediaPlayerState definiert.

Dieser Vorgang ist in den folgenden Fällen nützlich:

* Sie möchten eine `MediaPlayer` Instanz wiederverwenden, müssen jedoch eine neue Instanz laden `MediaResource` (Videoinhalt) und die vorherige Instanz ersetzen.

   Durch Zurücksetzen können Sie die `MediaPlayer` Instanz wiederverwenden, ohne dass die Freigabe von Ressourcen, die Wiederherstellung der Ressourcen `MediaPlayer`und die Neuzuweisung von Ressourcen mit Aufwand verbunden ist.

* Wenn der `MediaPlayer` Status FEHLER ist und gelöscht werden muss.

   >[!IMPORTANT]
   >
   >Dies ist die einzige Möglichkeit, sich vom FEHLER-Zustand zu erholen.

1. Aufruf `reset` zur Wiederherstellung des `MediaPlayer` nicht initialisierten Status:

   ```java
   void reset() throws IllegalStateException; 
   ```

1. Verwenden Sie `MediaPlayer.replaceCurrentResource` zum Laden eines anderen `MediaResource`.

   >[!TIP]
   >
   >Um einen Fehler zu löschen, müssen Sie dasselbe laden `MediaResource`.

1. Wenn Sie den `STATUS_CHANGED` Ereignis-Rückruf mit VORBEREITENDEM Status erhalten, wird die Wiedergabe Beginn.

## Eine MediaPlayer-Instanz und Ressourcen freigeben{#release-a-mediaplayer-instance-and-resources}

Sie sollten eine MediaPlayer-Instanz und Ressourcen freigeben, wenn Sie MediaResource nicht mehr benötigen.

Wenn Sie ein `MediaPlayer` Objekt freigeben, werden die mit diesem `MediaPlayer` Objekt verknüpften zugrunde liegenden Hardware-Ressourcen entzogen.

Es gibt einige Gründe, MediaPlayer zu veröffentlichen:

* Das Halten unnötiger Ressourcen kann sich auf die Leistung auswirken.
* Das Verlassen eines unnötigen `MediaPlayer` Objekts kann zu einem kontinuierlichen Akkuverbrauch von Mobilgeräten führen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es zu einem Wiedergabefehler für andere Anwendungen kommen.

1. Lassen Sie die `MediaPlayer`Lösung frei.

   ```java
   void release() throws IllegalStateException;
   ```

Nachdem die `MediaPlayer` Instanz freigegeben wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` Schnittstelle nach der Freigabe aufgerufen wird, wird eine `IllegalStateException` ausgelöst.