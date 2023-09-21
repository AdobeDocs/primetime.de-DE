---
description: Verwenden Sie die Hilfsklasse AuditudeSettings , die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungen-Metadaten einzurichten.
title: Einrichten von Anzeigeneinfüge-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Einrichten von Anzeigeneinfüge-Metadaten {#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings , die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungen-Metadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidungen wurden früher als Auditude bezeichnet.

Advertising-Metadaten befinden sich im `MediaResource.Metadata` -Eigenschaft. Beim Starten der Wiedergabe eines neuen Videos ist Ihre Anwendung für das Festlegen der richtigen Werbe-Metadaten verantwortlich.

1. Erstellen Sie die `AuditudeSettings` -Instanz.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Festlegen der Adobe Primetime-Anzeigenentscheidung `mediaID`, `zoneID`, `<ph conkeyref="phrases/primetime-sdk-name"/>`und den optionalen Targeting-Parametern.

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
   >Die Medien-ID wird von TVSDK als Zeichenfolge verwendet, die in einen md5-Wert konvertiert wird und für die `u` -Wert in der URL-Anfrage für Primetime-Anzeigenentscheidungen. Beispiel:
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Erstellen Sie eine `MediaResource` -Instanz mithilfe der Medien-Stream-URL und der zuvor erstellten Werbe-Metadaten.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Laden Sie die `MediaResource` -Objekt durch `MediaPlayer.replaceCurrentResource` -Methode.

   Die `MediaPlayer` startet das Laden und Verarbeiten des Medien-Stream-Manifests.

1. Wenn die Variable `MediaPlayer` Transitionen in den INITIALISIERTEN Status, um die Eigenschaften des Medienstreams in Form einer `MediaPlayerItem` -Instanz über die `MediaPlayer.CurrentItem` -Methode.
1. (Optional) Abfragen der `MediaPlayerItem` -Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er alternative Audiospuren hat oder ob der Stream geschützt ist.

   Diese Informationen können Ihnen bei der Vorbereitung der Benutzeroberfläche für die Wiedergabe helfen. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einfügen, das zwischen diesen Spuren umschaltet.

1. Aufruf `MediaPlayer.prepareToPlay` , um den Werbe-Workflow zu starten.

   Nachdem die Anzeigen aufgelöst und auf der Timeline platziert wurden, wird die `MediaPlayer` Transitionen zu `PREPARED` state.
1. Aufruf `MediaPlayer.play` , um die Wiedergabe zu starten.

TVSDK enthält jetzt Anzeigen, wenn Ihre Medien wiedergegeben werden.
