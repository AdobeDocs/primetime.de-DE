---
description: Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.
seo-description: Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.
seo-title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
title: Wiederverwenden oder Entfernen einer MediaPlayer-Instanz
uuid: da7b3468-3f0f-4025-927b-d47764a053af
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# Wiederverwenden oder Entfernen einer MediaPlayer-Instanz {#reuse-or-remove-a-mediaplayer-instance}

Sie können eine MediaPlayer-Instanz, die Sie nicht mehr benötigen, zurücksetzen, wiederverwenden oder freigeben.

## Zurücksetzen oder Wiederverwenden einer MediaPlayer-Instanz {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Wenn Sie eine `MediaPlayer`-Instanz zurücksetzen, wird sie an ihren nicht initialisierten IDLE-Status zurückgegeben, wie in `MediaPlayerStatus` definiert

* Sie möchten eine `MediaPlayer`-Instanz wiederverwenden, müssen jedoch eine neue `MediaResource` (Videoinhalt) laden und die vorherige Instanz ersetzen.

   Durch Zurücksetzen können Sie die `MediaPlayer`-Instanz wiederverwenden, ohne den Aufwand für die Freigabe von Ressourcen, das Neuerstellen der `MediaPlayer`-Instanz und das Neuzuordnen von Ressourcen zu verursachen.

* Wenn sich das `MediaPlayer` im FEHLER-Status befindet und gelöscht werden muss.

   >[!IMPORTANT]
   >
   >Dies ist die einzige Möglichkeit, um sich vom ERROR-Status zu erholen.

   1. Rufen Sie `reset` auf, um die `MediaPlayer`-Instanz auf ihren nicht initialisierten Status zurückzugeben:

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Verwenden Sie `MediaPlayer.replaceCurrentResource()`, um ein weiteres `MediaResource` zu laden.

      >[!NOTE]
      >
      >Um einen Fehler zu löschen, laden Sie dasselbe `MediaResource`.

   1. Wenn Sie den `STATUS_CHANGED`-Ereignis-Rückruf mit dem Status `PREPARED` erhalten, wird die Wiedergabe Beginn.

## Eine MediaPlayer-Instanz und Ressourcen {#section_13A0914AFF784943ABC343F7EB249C4E} freigeben

Sie sollten eine `MediaPlayer`-Instanz und Ressourcen freigeben, wenn Sie `MediaResource` nicht mehr benötigen.

Wenn Sie ein `MediaPlayer`-Objekt freigeben, werden die zugrunde liegenden Hardwareressourcen, die mit diesem `MediaPlayer`-Objekt verknüpft sind, dezugeordnet.

Es gibt einige Gründe für die Veröffentlichung eines `MediaPlayer`:

* Das Halten unnötiger Ressourcen kann sich auf die Leistung auswirken.
* Wenn Sie ein unnötiges `MediaPlayer`-Objekt instanziiert lassen, kann dies zu einem kontinuierlichen Akkuverbrauch für Mobilgeräte führen.
* Wenn mehrere Instanzen desselben Video-Codecs auf einem Gerät nicht unterstützt werden, kann es zu einem Wiedergabefehler für andere Anwendungen kommen.

* Lassen Sie `MediaPlayer` los.

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >Nachdem die `MediaPlayer`-Instanz freigegeben wurde, können Sie sie nicht mehr verwenden. Wenn eine Methode der `MediaPlayer`-Schnittstelle nach der Veröffentlichung aufgerufen wird, wird ein `MediaPlayerException`-Wert ausgegeben.