---
description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.
title: Anzeigeneinfügemetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---


# Anzeigeneinfügemetadaten {#ad-insertion-metadata}

Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.

TVSDK enthält die Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Primetime-Anzeigen-Entscheidungsserver enthalten, muss Ihre Anwendung die folgenden `AuditudeSettings`-Informationen bereitstellen:

* `mediaID`, was eine eindeutige ID für das abzuspielende Video darstellt.

   Der Herausgeber weist die mediaID beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad-Decision-Server zu. Diese ID wird von der Primetime-Anzeigenentscheidung verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

* Ihre `zoneID`, die der Adobe zugeordnet ist, kennzeichnet Ihre Firma oder Website.
* Die Domäne des zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

   Sie können diese Parameter abhängig von Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.

## Einrichten von Anzeigeneinfügemetadaten {#set-up-ad-insertion-metadata}

Verwenden Sie die Hilfsklasse AuditudeSettings , die die MetadataNode-Klasse erweitert, um Adobe Primetime-Anzeigenentscheidungsmetadaten einzurichten.

>[!TIP]
>
>Adobe Primetime-Anzeigenentscheidung war früher als Auditude bekannt.

Anzeigenmetadaten befinden sich in der Eigenschaft `MediaResource.metadata`. Beim Starten der Wiedergabe eines neuen Videos ist Ihre Anwendung dafür verantwortlich, die richtigen Anzeigenmetadaten festzulegen.

1. Erstellen Sie die Instanz `AuditudeSettings`.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Legen Sie die Adobe Primetime-Anzeigenbestimmungsparameter mediaID, zoneID, Domäne und die optionalen Targeting-Parameter fest.

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
   >Die Medien-ID wird von TVSDK als Zeichenfolge verwendet, die in einen md5-Wert konvertiert wird und für den `u`-Wert in der Primetime-Anfrage zur Auswahl der Anzeige verwendet wird. Beispiel:
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Erstellen Sie eine `MediaResource`-Instanz mithilfe der Medienstream-URL und der zuvor erstellten Anzeigenmetadaten.

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. Laden Sie das `MediaResource`-Objekt über die `MediaPlayer.replaceCurrentResource`-Methode.

   Die `MediaPlayer`-Beginn, die das Medienstream-Manifest laden und verarbeiten.

1. (Optional) Abfrage der `MediaPlayerItem`-Instanz, um zu sehen, ob der Stream live ist, unabhängig davon, ob er über alternative Audiospuren verfügt oder ob der Stream geschützt ist.

   Anhand dieser Informationen können Sie die Benutzeroberfläche für die Wiedergabe vorbereiten. Wenn Sie beispielsweise wissen, dass es zwei Audiospuren gibt, können Sie ein UI-Steuerelement einschließen, das zwischen diesen Spuren umschaltet.

1. Rufen Sie `MediaPlayer.prepareToPlay` auf, um den Werbe-Workflow Beginn.

   Nachdem die Anzeigen aufgelöst und auf der Zeitleiste platziert wurden, wird der Status `MediaPlayer` in den Status &quot;VORBEREITT&quot;Transition.
1. Rufen Sie `MediaPlayer.play` auf, um die Wiedergabe Beginn.

TVSDK enthält jetzt Anzeigen, wenn Ihre Medien wiedergegeben werden.