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
>* Ein `mediaID`, das den zu spielenden spezifischen Inhalt identifiziert.
>* Ihre `zoneID`, die Ihre Firma oder Website identifiziert.
>* Ihre Anzeigenserverdomäne, die die Domäne des zugewiesenen Anzeigenservers angibt.
>* Andere Targeting-Parameter.

>



## Primetime-Anzeigenservermetadaten {#section_86C4A3B2DF124770B9B7FD2511394313} einrichten

Ihre Anwendung muss TVSDK die erforderlichen `PTAuditudeMetadata`-Informationen bereitstellen, um eine Verbindung zum Anzeigen-Server herzustellen.

So richten Sie die Ad-Server-Metadaten ein:

1. Erstellen Sie eine Instanz von [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) und legen Sie deren Eigenschaften fest.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Stellen Sie die `PTAuditudeMetadata`-Instanz als Metadaten für die aktuellen `PTMediaPlayerItem`-Metadaten ein, indem Sie `PTAdResolvingMetadataKey` verwenden.

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   Hier ein Beispiel:

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

## Anzeigen im Vollbildmodus aktivieren {#section_6016E1DAF03645C8A8388D03C6AB7571}

Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.

Für Live-Inhalte verwendet TVSDK die Metadaten/Hinweise im Manifest, um zu bestimmen, wo Anzeigen platziert werden sollen. Manchmal ähneln Live-/Lineare Inhalte jedoch möglicherweise VOD-Inhalten. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird dem Live-Manifest ein `EXT-X-ENDLIST`-Tag angehängt. Bei HLS bedeutet das `EXT-X-ENDLIST`-Tag, dass der Stream ein VOD-Stream ist. TVSDK kann diesen Stream nicht automatisch von einem normalen VOD-Stream unterscheiden, um Anzeigen korrekt einzufügen.

Ihre Anwendung muss TVSDK mitteilen, ob der Inhalt live oder VOD ist, indem Sie `PTAdSignalingMode` angeben.

Bei einem FER-Stream sollte der Adobe Primetime-Ad-Entscheidungsserver nicht die Liste von Werbeunterbrechungen bereitstellen, die vor dem Starten der Wiedergabe in die Zeitleiste eingefügt werden müssen. Dies ist der typische Prozess für VOD-Inhalte. Stattdessen liest TVSDK durch Angabe eines anderen Signalisierungsmodus alle Cue-Points aus dem FER-Manifest und wechselt für jeden Cue-Point zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

Zusätzlich zu jeder Anforderung, die mit einem Cue-Point verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen auf.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie das `PTAdSignalingMode` mit `PTAdMetadata.signalingMode` an.

   Die gültigen Werte sind `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues` und `PTAdSignalingModeServerMap`.

   Sie müssen den Anzeigensignalisierungsmodus festlegen, bevor Sie `prepareToPlay` aufrufen. Nachdem TVSDK-Beginn Anzeigen auflösen und auf der Zeitleiste platzieren, werden Änderungen am Anzeigensignalisierungsmodus ignoriert. Legen Sie den Modus fest, wenn Sie die Anzeigenmetadaten für die Ressource erstellen.

1. Fahren Sie mit der Wiedergabe fort.

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

