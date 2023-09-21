---
description: Damit der Anzeigenauflöser funktioniert, erfordern Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte, um Ihre Verbindung zum Provider zu ermöglichen.
title: Anzeigeneinfüge-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Anzeigeneinfüge-Metadaten {#ad-insertion-metadata}

Damit der Anzeigenauflöser funktioniert, erfordern Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte, um Ihre Verbindung zum Provider zu ermöglichen.

TVSDK enthält die Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Primetime-Anzeigen-Decisioning-Server enthalten, muss Ihre Anwendung die folgenden erforderlichen Informationen bereitstellen `AuditudeSettings` Information:

* `mediaID`: eine eindeutige Kennung für das abzuspielende Video.

  Der Herausgeber weist die mediaID beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad Decisioning-Server zu. Diese ID wird von Primetime-Anzeigenentscheidungen verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

* Ihre `zoneID`, die von Adobe zugewiesen wird, identifiziert Ihr Unternehmen oder Ihre Website.
* Die Domäne Ihres zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

  Sie können diese Parameter entsprechend Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.

## Einrichten von Anzeigeneinfüge-Metadaten {#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings , die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungen-Metadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidungen wurden früher als Auditude bezeichnet.

Advertising-Metadaten befinden sich im `MediaResource.metadata` -Eigenschaft. Beim Starten der Wiedergabe eines neuen Videos ist Ihre Anwendung für das Festlegen der richtigen Werbe-Metadaten verantwortlich.

1. Erstellen Sie die `AuditudeSettings` -Instanz.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenentscheidung mediaID, zoneID, Domäne und die optionalen Targeting-Parameter fest.

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
   >Die Medien-ID wird von TVSDK als Zeichenfolge verwendet, die in einen md5-Wert konvertiert wird und für die `u` -Wert in der URL-Anfrage für Primetime-Anzeigenentscheidungen. Beispiel:
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Erstellen Sie eine `MediaResource` -Instanz mithilfe der Medien-Stream-URL und der zuvor erstellten Werbe-Metadaten.

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. Laden Sie die `MediaResource` -Objekt durch `MediaPlayer.replaceCurrentResource` -Methode.

   Die `MediaPlayer` startet das Laden und Verarbeiten des Medien-Stream-Manifests.

1. (Optional) Abfragen der `MediaPlayerItem` -Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er alternative Audiospuren aufweist oder ob der Stream geschützt ist.

   Diese Informationen können Ihnen bei der Vorbereitung der Benutzeroberfläche für die Wiedergabe helfen. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einfügen, das zwischen diesen Spuren umschaltet.

1. Aufruf `MediaPlayer.prepareToPlay` , um den Werbe-Workflow zu starten.

   Nachdem die Anzeigen aufgelöst und auf der Timeline platziert wurden, wird die `MediaPlayer` wechselt in den Status VORBEREITT .
1. Aufruf `MediaPlayer.play` , um die Wiedergabe zu starten.

TVSDK enthält jetzt Anzeigen, wenn Ihre Medien wiedergegeben werden.
