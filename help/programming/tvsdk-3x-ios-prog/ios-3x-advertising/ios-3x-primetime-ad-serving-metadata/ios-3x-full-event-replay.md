---
description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.
seo-description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.
seo-title: Primetime-Anzeigenservermetadaten
title: Primetime-Anzeigenservermetadaten
uuid: 61e224dd-551a-438f-8560-e64915087fef
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Aktivieren von Anzeigen bei vollständiger Wiedergabe im Ereignis {#section_6016E1DAF03645C8A8388D03C6AB7571}

Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.

Für Live-Inhalte verwendet TVSDK die Metadaten/Hinweise im Manifest, um zu bestimmen, wo Anzeigen platziert werden sollen. Manchmal ähneln Live-/Lineare Inhalte jedoch möglicherweise VOD-Inhalten. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird ein `EXT-X-ENDLIST` -Tag an das Live-Manifest angehängt. Bei HLS bedeutet das `EXT-X-ENDLIST` -Tag, dass der Stream ein VOD-Stream ist. TVSDK kann diesen Stream nicht automatisch von einem normalen VOD-Stream unterscheiden, um Anzeigen korrekt einzufügen.

Ihre Anwendung muss TVSDK mitteilen, ob der Inhalt live oder VOD ist, indem Sie die `PTAdSignalingMode`Angabe.

Bei einem FER-Stream sollte der Adobe Primetime-Anzeigenbestimmungsserver nicht die Liste von Werbeunterbrechungen bereitstellen, die vor dem Starten der Wiedergabe in die Zeitschiene eingefügt werden müssen. Dies ist der typische Prozess für VOD-Inhalte. Stattdessen liest TVSDK durch Angabe eines anderen Signalisierungsmodus alle Cue-Points aus dem FER-Manifest und wechselt für jeden Cue-Point zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

Zusätzlich zu jeder Anforderung, die mit einem Cue-Point verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen auf.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie die `PTAdSignalingMode` durch `PTAdMetadata.signalingMode`.

   Die gültigen Werte sind `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`und `PTAdSignalingModeServerMap`.

   Sie müssen den Anzeigensignalisierungsmodus vor dem Aufruf festlegen `prepareToPlay`. Nachdem TVSDK-Beginn Anzeigen auflösen und auf der Zeitleiste platzieren, werden Änderungen am Anzeigensignalisierungsmodus ignoriert. Legen Sie den Modus fest, wenn Sie die Anzeigenmetadaten für die Ressource erstellen.

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
