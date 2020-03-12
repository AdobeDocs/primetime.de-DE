---
description: Nachdem eine MediaPlayer-Ansicht zum Abspielen von Videos verwendet wurde, können Sie sie ausblenden und erneut anzeigen, indem Sie eine TVSDK-Methode oder manuell verwenden.
seo-description: Nachdem eine MediaPlayer-Ansicht zum Abspielen von Videos verwendet wurde, können Sie sie ausblenden und erneut anzeigen, indem Sie eine TVSDK-Methode oder manuell verwenden.
seo-title: Ansichten ausblenden
title: Ansichten ausblenden
uuid: 7cc02bf4-41ee-4af0-98ba-df070b50b88d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ansichten ausblenden{#hide-a-video-view}

Nachdem eine MediaPlayer-Ansicht zum Abspielen von Videos verwendet wurde, können Sie sie ausblenden und erneut anzeigen, indem Sie eine TVSDK-Methode oder manuell verwenden.

Sie müssen ein Video anhalten, bevor Sie es löschen oder von der Anzeige verschieben.
* Option 1: Löschen Sie den Videorahmen mit `MediaPlayer.clearVideo`&#x200B; und ersetzen Sie ihn später.
   * Halten Sie das Video an, das Sie ausblenden möchten.
   * Entfernen Sie den angezeigten Videorahmen durch Aufruf `MediaPlayer.clearVideo`.
   * Rufen Sie `MediaPlayer` oder rufen Sie an, um die Datei so zurückzusetzen, dass sie erneut wiedergegeben werden kann, `replaceCurrentResource` oder `replaceCurrentItem`.
* Option 2: Verschieben Sie die `MediaPlayer` Ansicht vom Bildschirm und verschieben Sie sie später wieder, ohne sie ersetzen zu müssen.
   * Halten Sie das Video an, das Sie ausblenden möchten.
   * Verschieben Sie die Ansicht aus der Bühne. Beispiel:

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * Um das Video erneut anzuzeigen, verschieben Sie die Ansicht zurück auf die Bühne.
