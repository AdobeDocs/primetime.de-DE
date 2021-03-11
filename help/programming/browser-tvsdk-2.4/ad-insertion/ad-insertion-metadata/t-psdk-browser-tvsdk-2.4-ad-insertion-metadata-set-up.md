---
description: Verwenden Sie die Hilfsklasse AuditudeSettings, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
title: Einrichten von Anzeigeneinfügemetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
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
