---
description: Verwenden Sie die Hilfsklasse AuditudeSettings , um Adobe Primetime-Anzeigenentscheidungen-Metadaten einzurichten.
title: Einrichten von Anzeigeneinfüge-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Einrichten von Anzeigeneinfüge-Metadaten{#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings , um Adobe Primetime-Anzeigenentscheidungen-Metadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidungen wurden früher als Auditude bezeichnet.

1. Erstellen Sie die `AuditudeSettings` -Instanz.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenentscheidung mediaID, zoneID, Domäne und die optionalen Targeting-Parameter fest.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Erstellen Sie eine `MediaResource` -Instanz mithilfe der Medien-Stream-URL und der zuvor erstellten Werbe-Metadaten.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Laden Sie die `MediaResource` -Objekt durch `MediaPlayer.replaceCurrentResource(resource)` -Methode.

   Die `MediaPlayer` startet das Laden und Verarbeiten des Medien-Stream-Manifests.

1. Wenn die Variable `MediaPlayer` Transitionen in den INITIALISIERTEN Status, um die Eigenschaften des Medienstreams in Form einer `MediaPlayerItem` -Instanz über die `MediaPlayer.CurrentItem` -Attribut.
1. (Optional) Abfragen der `MediaPlayerItem` -Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er alternative Audiospuren aufweist.

   Diese Informationen können Ihnen bei der Vorbereitung der Benutzeroberfläche für die Wiedergabe helfen. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einfügen, das zwischen diesen Spuren umschaltet.

1. Aufruf `MediaPlayer.prepareToPlay` , um den Werbe-Workflow zu starten.

   Nachdem die Anzeigen aufgelöst und auf der Timeline platziert wurden, wird die `  MediaPlayer ` wechselt in den Status VORBEREITT .
1. Aufruf `MediaPlayer.play` , um die Wiedergabe zu starten.
Browser TVSDK enthält jetzt Anzeigen, wenn Ihr Medium wiedergegeben wird.
