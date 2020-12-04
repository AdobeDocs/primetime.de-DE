---
description: Verwenden Sie die Hilfsklasse AuditudeSettings, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
seo-description: Verwenden Sie die Hilfsklasse AuditudeSettings, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
seo-title: Einrichten von Anzeigeneinfügemetadaten
title: Einrichten von Anzeigeneinfügemetadaten
uuid: fc37e0ae-6acf-4a78-a468-f7b5b123b45e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Einrichten von Anzeigeneinfügemetadaten{#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.

>[!TIP]
>
>Adobe Primetime Ad Decision wurde früher als Auditude bezeichnet.

1. Erstellen Sie die Instanz `AuditudeSettings`.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenbestimmungsparameter mediaID, zoneID, Domäne und die optionalen Targeting-Parameter fest.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Erstellen Sie eine `MediaResource`-Instanz mithilfe der Medienstream-URL und der zuvor erstellten Anzeigenmetadaten.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Laden Sie das `MediaResource`-Objekt über die `MediaPlayer.replaceCurrentResource(resource)`-Methode.

   Die `MediaPlayer`-Beginn, die das Medienstream-Manifest laden und verarbeiten.

1. Wenn `MediaPlayer` den INITIALIZED-Status Transition, erhalten Sie die Medienstream-Eigenschaften in Form einer `MediaPlayerItem`-Instanz über das `MediaPlayer.CurrentItem`-Attribut.
1. (Optional) Abfrage der `MediaPlayerItem`-Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er über alternative Audiospuren verfügt.

   Anhand dieser Informationen können Sie die Benutzeroberfläche für die Wiedergabe vorbereiten. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einschließen, das zwischen diesen Spuren umschaltet.

1. Rufen Sie `MediaPlayer.prepareToPlay` auf, um den Werbe-Workflow Beginn.

   Nachdem die Anzeigen aufgelöst und auf der Zeitleiste platziert wurden, wird der Status `  MediaPlayer ` in den Status &quot;VORBEREITT&quot;Transition.
1. Rufen Sie `MediaPlayer.play` auf, um die Wiedergabe Beginn.
Browser TVSDK enthält jetzt Anzeigen bei der Wiedergabe Ihrer Medien.
