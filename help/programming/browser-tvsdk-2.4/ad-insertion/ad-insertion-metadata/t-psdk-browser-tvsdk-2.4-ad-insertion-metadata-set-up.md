---
description: Verwenden Sie die Hilfsklasse AuditudeSettings, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
seo-description: Verwenden Sie die Hilfsklasse AuditudeSettings, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
seo-title: Einrichten von Anzeigeneinfügemetadaten
title: Einrichten von Anzeigeneinfügemetadaten
uuid: fc37e0ae-6acf-4a78-a468-f7b5b123b45e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Einrichten von Anzeigeneinfügemetadaten{#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidungen wurden zuvor als Auditude bezeichnet.

1. Erstellen Sie die `AuditudeSettings` Instanz.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenentscheidungsparameter mediaID, zoneID, Domäne und die optionalen Targeting-Parameter fest.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Erstellen Sie eine `MediaResource` Instanz mit der Medienstream-URL und den zuvor erstellten Anzeigenmetadaten.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Laden Sie das `MediaResource` Objekt über die `MediaPlayer.replaceCurrentResource(resource)` Methode.

   Die `MediaPlayer` Beginn, die das Medienstream-Manifest laden und verarbeiten.

1. Wenn die `MediaPlayer` Transitionen zum INITIALIZED-Status erfolgen, erhalten Sie die Medienstream-Eigenschaften in Form einer `MediaPlayerItem` Instanz über das `MediaPlayer.CurrentItem` Attribut.
1. (Optional) Abfrage der `MediaPlayerItem` Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er über alternative Audiospuren verfügt.

   Anhand dieser Informationen können Sie die Benutzeroberfläche für die Wiedergabe vorbereiten. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einschließen, das zwischen diesen Spuren umschaltet.

1. Rufen Sie `MediaPlayer.prepareToPlay` an, um den Werbe-Workflow Beginn.

   Nachdem die Anzeigen aufgelöst und auf der Zeitleiste platziert wurden, werden die `  MediaPlayer ` Transitionen in den Status &quot;VORBEREITT&quot;geändert.
1. Aufruf `MediaPlayer.play` zum Beginn der Wiedergabe.
Browser TVSDK enthält jetzt Anzeigen bei der Wiedergabe Ihrer Medien.
