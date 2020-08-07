---
description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.
seo-description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.
seo-title: Primetime-Anzeigenservermetadaten
title: Primetime-Anzeigenservermetadaten
uuid: 314f14c0-4da4-4da6-96f9-5a5ffea22a99
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# Übersicht {#primetime-ad-server-metadata-overview}

TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.

>[!NOTE]
>
>Bevor Sie Werbung in Ihren Videoinhalt aufnehmen können, geben Sie die folgenden Metadaten an:
>
>* Eine `mediaID`, die den zu spielenden Inhalt identifiziert.
>* Ihre `zoneID`, die Ihre Firma oder Website identifiziert.
>* Ihre Anzeigenserverdomäne, die die Domäne des zugewiesenen Anzeigenservers angibt.
>* Andere Targeting-Parameter.

>



## Einrichten von Primetime-Anzeigenservermetadaten {#section_86C4A3B2DF124770B9B7FD2511394313}

Your application must provide TVSDK with the required `PTAuditudeMetadata` information to connect to the ad server.

So richten Sie die Ad-Server-Metadaten ein:

1. Create an instance of [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) and set its properties.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Set the `PTAuditudeMetadata` instance as metadata for the current `PTMediaPlayerItem` metadata by using `PTAdResolvingMetadataKey`.

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   Here is an example:

   ```
   PTMetadata *metadata = [self createMetadata]; 
   PTMediaPlayerItem *item =  
     [[[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease]; 
   
   - (PTMetadata *) createMetadata { 
       PTMetadata* metadata = [[[PTMetadata alloc] init] autorelease]; 
   
       PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
       adMetadata.zoneId = yourZoneID; 
       adMetadata.domain = yourAdServerDomain; 
   
       [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
       return metadata; 
   }
   ```

## Enable ads in full-event replay {#section_6016E1DAF03645C8A8388D03C6AB7571}

Full-event replay (FER) is a VOD asset that acts as a live/DVR asset, so your application must take steps to ensure that ads are placed correctly.

For live content, TVSDK uses the metadata/cues in the manifest to determine where to place ads. However, sometimes live/linear content might resemble VOD content. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird ein `EXT-X-ENDLIST` -Tag an das Live-Manifest angehängt. For HLS, the `EXT-X-ENDLIST` tag means that the stream is a VOD stream. TVSDK cannot automatically differentiate this stream from a normal VOD stream to correctly insert ads.

Your application must tell TVSDK whether the content is live or VOD by specifying the `PTAdSignalingMode`.

Bei einem FER-Stream sollte der Adobe Primetime-Ad-Entscheidungsserver nicht die Liste von Werbeunterbrechungen bereitstellen, die vor dem Starten der Wiedergabe in die Zeitleiste eingefügt werden müssen. This is the typical process for VOD content. Stattdessen liest TVSDK durch Angabe eines anderen Signalisierungsmodus alle Cue-Points aus dem FER-Manifest und wechselt für jeden Cue-Point zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

Zusätzlich zu jeder Anforderung, die mit einem Cue-Point verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen auf.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie die `PTAdSignalingMode` durch `PTAdMetadata.signalingMode`.

   Die gültigen Werte sind `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`und `PTAdSignalingModeServerMap`.

   You must set the ad signaling mode before calling `prepareToPlay`. After TVSDK starts to resolve and place ads on the timeline, changes to the ad signaling mode are ignored. Legen Sie den Modus fest, wenn Sie die Anzeigenmetadaten für die Ressource erstellen.

1. Continue to playback.

   ```
      PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.zoneId = your-auditude-zone-id; 
   adMetadata.domain = @"your-auditude-domain"; 
   //adMetadata.enableDVRAds = YES; // FOR LIVE DVR case 
   //adMetadata.signalingMode = PTAdSignalingModeManifestCues;  
   // FOR VOD FER case 
   NSMutableDictionary *targetingParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [targetingParameters setValue:@"ipad" forKey:@"device"]; 
   [targetingParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.targetingParameters = targetingParameters; 
   NSMutableDictionary *customParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [customParameters setValue:@"your-media-id" forKey:@"NW_ID"]; 
   [customParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.customParameters = customParameters; 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   ```

