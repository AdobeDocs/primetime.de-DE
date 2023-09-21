---
description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live-/Linearströme.
title: Primetime-Anzeigenserver-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Aktivieren von Anzeigen bei vollständiger Ereigniswiedergabe {#section_6016E1DAF03645C8A8388D03C6AB7571}

Die Wiederholung eines vollständigen Ereignisses (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Maßnahmen ergreifen, um sicherzustellen, dass Anzeigen korrekt platziert werden.

Für Live-Inhalte verwendet TVSDK die Metadaten/Hinweise im Manifest, um zu bestimmen, wo Anzeigen platziert werden sollen. Manchmal ähneln Live-/lineare Inhalte jedoch möglicherweise VOD-Inhalten. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird ein `EXT-X-ENDLIST` -Tag an das Live-Manifest angehängt. Bei HLS muss die Variable `EXT-X-ENDLIST` -Tag bedeutet, dass der Stream ein VOD-Stream ist. TVSDK kann diesen Stream nicht automatisch von einem normalen VOD-Stream unterscheiden, um Anzeigen korrekt einzufügen.

Ihre Anwendung muss TVSDK mitteilen, ob der Inhalt live oder VOD ist, indem Sie die `PTAdSignalingMode`.

Bei einem FER-Stream sollte der Adobe Primetime-Ad Decisioning-Server nicht die Liste der Werbeunterbrechungen bereitstellen, die in die Timeline eingefügt werden müssen, bevor die Wiedergabe gestartet wird. Dies ist der typische Prozess für VOD-Inhalte. Stattdessen liest TVSDK durch Angabe eines anderen Signalmodus alle Cue-Punkte aus dem FER-Manifest und geht für jeden Cue-Punkt zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

Zusätzlich zu jeder Anfrage, die mit einem Cue-Punkt verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen vor.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie die `PTAdSignalingMode` mithilfe von `PTAdMetadata.signalingMode`.

   Die gültigen Werte sind `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`, und `PTAdSignalingModeServerMap`.

   Sie müssen den Anzeigenanzeigemodus festlegen, bevor Sie `prepareToPlay`. Wenn TVSDK beginnt, Anzeigen aufzulösen und auf der Timeline zu platzieren, werden Änderungen am Anzeigenanzeigemodus ignoriert. Legen Sie den Modus fest, wenn Sie die Werbe-Metadaten für die Ressource erstellen.

1. Wiedergabe fortsetzen.

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
