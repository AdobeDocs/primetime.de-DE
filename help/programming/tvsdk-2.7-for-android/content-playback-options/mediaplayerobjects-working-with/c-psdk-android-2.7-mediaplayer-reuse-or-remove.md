---
description: Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.
seo-description: Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.
seo-title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
uuid: da7b3468-3f0f-4025-927b-d47764a053af
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Wiederverwenden oder Entfernen einer MediaPlayer-Instanz {#reuse-or-remove-a-mediaplayer-instance}

Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.

## Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Wenn Sie eine `MediaPlayer` Instanz zurücksetzen, wird sie auf ihren nicht initialisierten IDLE-Status zurückgesetzt, wie in `MediaPlayerStatus`

* Sie möchten eine `MediaPlayer` Instanz wiederverwenden, müssen jedoch eine neue Instanz laden `MediaResource` (Videoinhalt) und die vorherige Instanz ersetzen.

   Durch Zurücksetzen können Sie die `MediaPlayer` Instanz wiederverwenden, ohne dass die Freigabe von Ressourcen, die Wiederherstellung der Ressourcen `MediaPlayer`und die Neuzuweisung von Ressourcen mit Aufwand verbunden ist.

* Wenn sich der Status &quot;FEHLER&quot; `MediaPlayer` befindet und gelöscht werden muss.

   >[!IMPORTANT]
   >
   >Dies ist die einzige Möglichkeit, um sich vom ERROR-Status zu erholen.

   1. Aufruf `reset` zur Rückgabe des `MediaPlayer` Status &quot;nicht initialisiert&quot;:

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Verwenden Sie `MediaPlayer.replaceCurrentResource()` zum Laden eines anderen `MediaResource`.

      >[!NOTE]
      >
      >Um einen Fehler zu löschen, müssen Sie dasselbe laden `MediaResource`.

   1. Wenn Sie den `STATUS_CHANGED` Ereignis-Rückruf mit dem `PREPARED` Status erhalten, wird die Wiedergabe Beginn.

## Eine MediaPlayer-Instanz und Ressourcen freigeben {#section_13A0914AFF784943ABC343F7EB249C4E}

Sie sollten eine `MediaPlayer` Instanz und Ressourcen freigeben, wenn Sie die nicht mehr benötigen `MediaResource`.

Wenn Sie ein `MediaPlayer` Objekt freigeben, werden die mit diesem `MediaPlayer` Objekt verknüpften zugrunde liegenden Hardware-Ressourcen entzogen.

Es gibt einige Gründe für die Veröffentlichung eines `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann sich auf die Leistung auswirken.
* Das Verlassen eines unnötigen `MediaPlayer` Objekts instanziiert kann zu einem kontinuierlichen Akkuverbrauch von Mobilgeräten führen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es zu einem Wiedergabefehler für andere Anwendungen kommen.

* Lassen Sie die `MediaPlayer`Lösung frei.

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >Nachdem die `MediaPlayer` Instanz freigegeben wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer` Schnittstelle nach der Freigabe aufgerufen wird, wird eine `MediaPlayerException` ausgelöst.