---
description: Nachdem eine MediaPlayer-Ansicht zum Abspielen von Videos verwendet wurde, können Sie sie ausblenden und erneut anzeigen, indem Sie eine TVSDK-Methode oder manuell verwenden.
title: Ansichten ausblenden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 1%

---


# Eine Video-Ansicht{#hide-a-video-view} ausblenden

Nachdem eine MediaPlayer-Ansicht zum Abspielen von Videos verwendet wurde, können Sie sie ausblenden und erneut anzeigen, indem Sie eine TVSDK-Methode oder manuell verwenden.

Sie müssen ein Video anhalten, bevor Sie es löschen oder von der Anzeige verschieben.
* Option 1: Löschen Sie den Videobild mit `MediaPlayer.clearVideo` &#x200B; und ersetzen Sie ihn später.
   * Halten Sie das Video an, das Sie ausblenden möchten.
   * Entfernen Sie den angezeigten Videobild, indem Sie `MediaPlayer.clearVideo` aufrufen.
   * Rufen Sie `replaceCurrentResource` oder `replaceCurrentItem` auf, um das `MediaPlayer` so zurückzusetzen, dass es erneut wiedergegeben werden kann.
* Option 2: Verschieben Sie die `MediaPlayer`-Ansicht vom Bildschirm und verschieben Sie sie später zurück, ohne sie ersetzen zu müssen.
   * Halten Sie das Video an, das Sie ausblenden möchten.
   * Verschieben Sie die Ansicht aus der Bühne. Beispiel:

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * Um das Video erneut anzuzeigen, verschieben Sie die Ansicht zurück auf die Bühne.
