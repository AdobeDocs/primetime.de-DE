---
description: Verwenden Sie die Hilfsklasse AuditudeSettings, die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
seo-description: Verwenden Sie die Hilfsklasse AuditudeSettings, die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
seo-title: Einrichten von Anzeigeneinfügemetadaten
title: Einrichten von Anzeigeneinfügemetadaten
uuid: 5c807fad-4927-4547-b58c-f37e505e651c
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Einrichten von Anzeigeneinfügemetadaten {#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings, die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidung wurde zuvor als Auditude bezeichnet.

Anzeigenmetadaten befinden sich in der `MediaResource.Metadata` Eigenschaft. Beim Starten der Wiedergabe eines neuen Videos ist Ihre Anwendung dafür verantwortlich, die richtigen Anzeigenmetadaten festzulegen.

1. Erstellen Sie die `AuditudeSettings` Instanz.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenentscheidungsparameter `mediaID`, `zoneID`und `<ph conkeyref="phrases/primetime-sdk-name"/>`die optionalen Targeting-Parameter fest.

   ```java
   auditudeSettings.setZoneId("yourZoneId"); 
   auditudeSettings.setMediaId("yourVideoId"); 
   auditudeSettings.setDefaultMediaId("defVideoId"); 
   auditudeSettings.setDomain("yourAuditudeDomain"); 
   
   // Optionally set user agent  
   auditudeSettings.setUserAgent("yourUserAgent"); 
   
   Metadata targetingParameters = new Metadata(); 
   targetingParameters.setValue("desired_param", "desired_value"); 
   auditudeSettings.setTargetingParameters(targetingParameters);
   ```

   >[!TIP]
   >
   >Die Medien-ID wird von TVSDK als Zeichenfolge verwendet, die in einen md5-Wert konvertiert wird und für den `u` Wert in der Primetime-Anfrage zur Auswahl der URL verwendet wird. Beispiel:
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Erstellen Sie eine `MediaResource` Instanz mit der Medienstream-URL und den zuvor erstellten Anzeigenmetadaten.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Laden Sie das `MediaResource` Objekt über die `MediaPlayer.replaceCurrentResource` Methode.

   Die `MediaPlayer` Beginn, die das Medienstream-Manifest laden und verarbeiten.

1. Wenn die `MediaPlayer` Transitionen zum INITIALIZED-Status erfolgen, erhalten Sie die Medienstream-Eigenschaften in Form einer `MediaPlayerItem` Instanz mithilfe der `MediaPlayer.CurrentItem` Methode.
1. (Optional) Abfrage der `MediaPlayerItem` Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er über alternative Audiospuren verfügt oder ob der Stream geschützt ist.

   Anhand dieser Informationen können Sie die Benutzeroberfläche für die Wiedergabe vorbereiten. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einschließen, das zwischen diesen Spuren umschaltet.

1. Rufen Sie `MediaPlayer.prepareToPlay` an, um den Werbe-Workflow Beginn.

   Nachdem die Anzeigen aufgelöst und auf der Zeitleiste platziert wurden, werden die `MediaPlayer` Transitionen zum `PREPARED` Status angezeigt.
1. Aufruf `MediaPlayer.play` zum Beginn der Wiedergabe.

TVSDK enthält jetzt Anzeigen, wenn Ihre Medien wiedergegeben werden.