---
description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-title: Anzeigeneinfügemetadaten
title: Anzeigeneinfügemetadaten
uuid: 3eb024c3-4bb5-4bee-943e-fe0c60379e60
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Anzeigeneinfügemetadaten {#ad-insertion-metadata}

Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.

TVSDK enthält die Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Primetime-Anzeigen-Entscheidungsserver enthalten, muss Ihre Anwendung die folgenden erforderlichen `AuditudeSettings` Informationen bereitstellen:

* `mediaID`, was eine eindeutige ID für das abzuspielende Video darstellt.

   Der Herausgeber weist die mediaID beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad-Entscheidungsserver zu. Diese ID wird von der Primetime-Anzeigenentscheidung verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

* Ihre von Adobe zugewiesene `zoneID`Firma oder Website wird von Ihnen identifiziert.
* Die Domäne des zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

   Sie können diese Parameter abhängig von Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.

## Einrichten von Anzeigeneinfügemetadaten {#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings , die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidung wurde zuvor als Auditude bezeichnet.

Anzeigenmetadaten befinden sich in der `MediaResource.metadata` Eigenschaft. Beim Starten der Wiedergabe eines neuen Videos ist Ihre Anwendung dafür verantwortlich, die richtigen Anzeigenmetadaten festzulegen.

1. Erstellen Sie die `AuditudeSettings` Instanz.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenentscheidungsparameter mediaID, zoneID, Domäne und die optionalen Targeting-Parameter fest.

   ```
   auditudeSettings.zoneId = "yourZoneID"; 
   auditudeSettings.mediaId = "media_identifier"; 
   auditudeSettings.domain = "yourAuditudeDomain"; 
   var targetingInfo:Metadata = new Metadata(); 
   targetingInfo.setValue("yourParamName", "yourParamValue"); 
   auditudeSettings.targetingInfo = targetingInfo;
   ```

   >[!TIP]
   >
   >Die Medien-ID wird von TVSDK als Zeichenfolge verwendet, die in einen md5-Wert konvertiert wird und für den `u` Wert in der Primetime-Anfrage zur Auswahl der URL verwendet wird. Beispiel:
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Erstellen Sie eine `MediaResource` Instanz mit der Medienstream-URL und den zuvor erstellten Anzeigenmetadaten.

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. Laden Sie das `MediaResource` Objekt über die `MediaPlayer.replaceCurrentResource` Methode.

   Die `MediaPlayer` Beginn, die das Medienstream-Manifest laden und verarbeiten.

1. (Optional) Abfrage der `MediaPlayerItem` Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er über alternative Audiospuren verfügt oder ob der Stream geschützt ist.

   Anhand dieser Informationen können Sie die Benutzeroberfläche für die Wiedergabe vorbereiten. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einschließen, das zwischen diesen Spuren umschaltet.

1. Rufen Sie `MediaPlayer.prepareToPlay` an, um den Werbe-Workflow Beginn.

   Nachdem die Anzeigen aufgelöst und auf der Zeitleiste platziert wurden, werden die `MediaPlayer` Transitionen in den Status &quot;VORBEREITT&quot;geändert.
1. Aufruf `MediaPlayer.play` zum Beginn der Wiedergabe.

TVSDK enthält jetzt Anzeigen, wenn Ihre Medien wiedergegeben werden.