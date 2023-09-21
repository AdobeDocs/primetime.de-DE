---
description: Nachdem eine MediaPlayer-Ansicht zum Abspielen von Videos verwendet wurde, können Sie sie ausblenden und erneut anzeigen, indem Sie eine TVSDK-Methode oder manuell verwenden.
title: Ausblenden einer Videoansicht
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Ausblenden einer Videoansicht{#hide-a-video-view}

Nachdem eine MediaPlayer-Ansicht zum Abspielen von Videos verwendet wurde, können Sie sie ausblenden und erneut anzeigen, indem Sie eine TVSDK-Methode oder manuell verwenden.

Sie müssen ein Video anhalten, bevor Sie es löschen oder von der Anzeige verschieben.
* Option 1: Löschen Sie den Videobild mit `MediaPlayer.clearVideo`&#x200B; und ersetzen Sie den Rahmen später.
   * Halten Sie das Video an, das Sie ausblenden möchten.
   * Entfernen Sie den angezeigten Video-Frame, indem Sie `MediaPlayer.clearVideo`.
   * So setzen Sie die `MediaPlayer` , damit es erneut wiedergegeben werden kann, rufen Sie `replaceCurrentResource` oder `replaceCurrentItem`.
* Option 2: Verschieben Sie die `MediaPlayer` Sie können den Bildschirm anzeigen und ihn später wieder verschieben, ohne ihn ersetzen zu müssen.
   * Halten Sie das Video an, das Sie ausblenden möchten.
   * Verschieben Sie die Ansicht aus der Bühne. Beispiel:

     ```
     view.x = -300; 
     view.y = -300;
     ```

   * Um das Video erneut anzuzeigen, verschieben Sie die Ansicht zurück in die Bühne.
