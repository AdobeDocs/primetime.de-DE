---
description: Verwenden Sie die Hilfsklasse AuditudeSettings, die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.
title: Einrichten von Anzeigeneinfügemetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Einrichten von Anzeigeneinfügemetadaten {#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse `AuditudeSettings`, die die `MetadataNode`-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidung war früher als Auditude bekannt.

Anzeigenmetadaten befinden sich in der Eigenschaft `MediaResource.Metadata`. Beim Starten der Wiedergabe eines neuen Videos ist Ihre Anwendung dafür verantwortlich, die richtigen Anzeigenmetadaten festzulegen.

1. Erstellen Sie die Instanz `AuditudeSettings`.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenentscheidungen `mediaID`, `zoneID`, `<ph conkeyref="phrases/primetime-sdk-name"/>` und die optionalen Targeting-Parameter fest.

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
   >Die Medien-ID wird von TVSDK als Zeichenfolge verwendet, die in einen md5-Wert konvertiert wird und für den `u`-Wert in der Primetime-Anfrage zur Auswahl der Anzeige verwendet wird. Beispiel:
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Erstellen Sie eine `MediaResource`-Instanz mithilfe der Medienstream-URL und der zuvor erstellten Anzeigenmetadaten.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Laden Sie das `MediaResource`-Objekt über die `MediaPlayer.replaceCurrentResource`-Methode.

   Die `MediaPlayer`-Beginn, die das Medienstream-Manifest laden und verarbeiten.

1. Wenn `MediaPlayer` den INITIALIZED-Status Transition, rufen Sie die Medienstream-Eigenschaften mithilfe der `MediaPlayer.CurrentItem`-Methode in Form einer `MediaPlayerItem`-Instanz ab.
1. (Optional) Abfrage der `MediaPlayerItem`-Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er über alternative Audiospuren verfügt oder ob der Stream geschützt ist.

   Anhand dieser Informationen können Sie die Benutzeroberfläche für die Wiedergabe vorbereiten. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einschließen, das zwischen diesen Spuren umschaltet.

1. Rufen Sie `MediaPlayer.prepareToPlay` auf, um den Werbe-Workflow Beginn.

   Nachdem die Anzeigen aufgelöst und auf der Zeitleiste platziert wurden, wird der Status `MediaPlayer` in `PREPARED` Transition.
1. Rufen Sie `MediaPlayer.play` auf, um die Wiedergabe Beginn.
TVSDK enthält jetzt Anzeigen, wenn Ihre Medien wiedergegeben werden.
