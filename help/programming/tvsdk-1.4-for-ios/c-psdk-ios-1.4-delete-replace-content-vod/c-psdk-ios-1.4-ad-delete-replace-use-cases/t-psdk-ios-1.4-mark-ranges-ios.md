---
description: 'null'
seo-description: 'null'
seo-title: Markierbereiche
title: Markierbereiche
uuid: 994a8f07-0951-47ec-b21a-d74c9eeefd74
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Markierbereiche{#mark-ranges}

So implementieren Sie `PTTimeRangeCollection` und markieren Inhaltsbereiche als Anzeigen:
1. Bereiten Sie das `PTTimeRangeCollection` vor.
1. Legen Sie den Typ von `PTTimeRangeCollection` auf `PTTimeRangeCollectionTypeMarkRanges` fest.

   Dieser Schritt benachrichtigt TVSDK, dass die benutzerdefinierten Bereiche wie Anzeigen behandelt werden müssen.

   ```
   #define PSDK_TIMESCALE 100000 
   
   NSArray *ranges =  @[ 
     [PTReplacementRange  
       replacementRangeWithRange:CMTimeRangeMake(CMTimeMakeWithSeconds 
         (0, PSDK_TIMESCALE),CMTimeMakeWithSeconds(60, AD_TIMESCALE))], 
     [PTReplacementRange  
       replacementRangeWithRange:CMTimeRangeMake(CMTimeMakeWithSeconds 
         (120, PSDK_TIMESCALE),CMTimeMakeWithSeconds(60, AD_TIMESCALE))] 
   ]; 
   
   PTTimeRangeCollection *timeRangeCollection =  
     [[PTTimeRangeCollection alloc] initWithRanges:ranges  
       type:PTTimeRangeCollectionTypeMarkRanges];
   ```

1. Erstellen Sie `PTAdMetadata` und legen Sie `PTTimeRangeCollection` fest.

   ```
   // Create the PTPlayerItem metadata 
   PTMetadata *metadata = [[PTMetadata alloc] init]; 
   
   // Create the Ad metadata 
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init]; 
   adMetadata.timeRangeCollection = timerangeCollection; 
   
   //Set Ad metadata 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
   //Create PTMediaPlayerItem 
   PTMediaPlayerItem *playerItem = [[[PTMediaPlayerItem alloc] initWithUrl:mediaUrl 
                                                                   mediaId:mediaId 
                                                                  metadata:metadata];
   ```

1. Erstellen Sie die Wiedergabe des Players und Beginns.

   ```
   //Create PTMediaPlayer using the created PTMediaPlayer 
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:playerItem]; 
   
   //Add player to the player UIView 
   [self.playerView addSubview:(UIView *)player.view]; 
   
   //Start playback 
   [player play];
   ```

## Ersetzen Sie Bereiche{#replace-ranges}

So implementieren Sie die Inhaltsbereiche `PTTimeRangeCollection` und löschen Sie sie als Anzeigen:
1. `PTTimeRangeCollection` vorbereiten.
1. Legen Sie den Typ von `PTTimeRangeCollection` auf `PTTimeRangeCollectionTypeReplaceRanges` fest.

   Dieser Schritt benachrichtigt TVSDK, dass die bereitgestellten Bereiche durch alternative Inhalte (Anzeigen) ersetzt werden müssen.

   ```
   #define PSDK_TIMESCALE 100000 
   
   NSArray *ranges =  @[ 
     [PTReplacementRange replacementRangeWithRange:CMTimeRangeMake(CMTimeMakeWithSeconds 
       (0, PSDK_TIMESCALE),CMTimeMakeWithSeconds(60, AD_TIMESCALE))  
       replacementDuration:CMTimeMakeWithSeconds(30, AD_TIMESCALE)], 
     [PTReplacementRange replacementRangeWithRange:CMTimeRangeMake(CMTimeMakeWithSeconds 
       (120, PSDK_TIMESCALE),CMTimeMakeWithSeconds(60, AD_TIMESCALE))  
       replacementDuration:CMTimeMakeWithSeconds(30, AD_TIMESCALE)] 
                       ]; 
   
   PTTimeRangeCollection *timeRangeCollection =  
     [[PTTimeRangeCollection alloc] initWithRanges:ranges  
                                              type:PTTimeRangeCollectionTypeReplaceRanges];
   ```

   >[!TIP]
   >
   >Das Argument `replacementDuration` ist optional. Wenn sie nicht definiert ist, bestimmt das `AdServer` die Dauer der Werbeunterbrechung.

1. Erstellen Sie `PTAdMetadata` und legen Sie `PTTimeRangeCollection` fest.

   ```
   //Create the PTPlayerItem metadata 
   PTMetadata *metadata = [[PTMetadata alloc] init]; 
   
   //Create the Ad metadata 
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init]; 
   adMetadata.timeRangeCollection = timerangeCollection; 
   adMetadata.zoneId = adZoneId; 
   adMetadata.domain = adDomain; 
   adMetadata.signalingMode = PTAdSignalingModeCustomRanges; 
   
   //Set Ad metadata 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
   //Create PTMediaPlayerItem 
   PTMediaPlayerItem *playerItem = [[[PTMediaPlayerItem alloc] initWithUrl:mediaUrl 
                                                                   mediaId:mediaId 
                                                                  metadata:metadata];
   ```

   >[!TIP]
   >
   >Obwohl `signalingMode` als `PTAdSignalingModeCustomRanges` eingestellt ist, wird dieser Anzeigensignalisierungsmodus automatisch eingestellt, wenn `PTTimeRangeCollection` des Typs `PTTimeRangeCollectionTypeReplace` eingestellt wird.

1. Erstellen Sie die Wiedergabe des Players und Beginns.

   ```
   //Create PTMediaPlayer using the created PTMediaPlayer 
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:playerItem]; 
   
   //Add player to the player UIView 
   [self.playerView addSubview:(UIView *)player.view]; 
   
   //Start playback 
   [player play];
   ```

## Bereiche {#delete-ranges} löschen

So implementieren Sie die Inhaltsbereiche `PTTimeRangeCollection` und löschen Sie sie als Anzeigen:
1. Bereiten Sie das `PTTimeRangeCollection` vor.
1. Stellen Sie den Typ von `PTTimeRangeCollection` auf `PTTimeRangeCollectionTypeDeleteRanges` ein, wodurch TVSDK benachrichtigt wird, dass die bereitgestellten Bereiche gelöscht werden müssen.

   ```
   #define PSDK_TIMESCALE 100000 
   
   NSArray *ranges =  @[ 
     [PTReplacementRange replacementRangeWithRange:CMTimeRangeMake(CMTimeMakeWithSeconds 
       (0, PSDK_TIMESCALE),CMTimeMakeWithSeconds(60, AD_TIMESCALE))], 
     [PTReplacementRange replacementRangeWithRange:CMTimeRangeMake(CMTimeMakeWithSeconds 
       (120, PSDK_TIMESCALE),CMTimeMakeWithSeconds(60, AD_TIMESCALE))] 
   ]; 
   
   PTTimeRangeCollection *timeRangeCollection =  
     [[PTTimeRangeCollection alloc] initWithRanges:ranges  
                                              type:PTTimeRangeCollectionTypeDeleteRanges];
   ```

1. Erstellen Sie `PTAdMetadata` und legen Sie `PTTimeRangeCollection` fest.

   ```
   //Create the PTPlayerItem metadata 
   PTMetadata *metadata = [[PTMetadata alloc] init]; 
   
   //Create the Ad metadata 
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init]; 
   adMetadata.timeRangeCollection = timerangeCollection; 
   adMetadata.zoneId = adZoneId; 
   adMetadata.domain = adDomain; 
   adMetadata.signalingMode = PTAdSignalingModeServerMap; 
   
   //Set Ad metadata 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
   //Create PTMediaPlayerItem 
   PTMediaPlayerItem *playerItem = [[[PTMediaPlayerItem alloc] initWithUrl:mediaUrl 
                                                                   mediaId:mediaId 
                                                                  metadata:metadata];
   ```

   >[!TIP]
   >
   >Das Einfügen von Anzeigen erfolgt nach dem Löschen der benutzerdefinierten Bereiche basierend auf dem `PTAdMetadata` und dem aktuellen `PTAdSignalingMode`.

1. Erstellen Sie die Wiedergabe des Players und Beginns.

   ```
   //Create PTMediaPlayer using the created PTMediaPlayer 
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:playerItem]; 
   
   //Add player to the player UIView 
   [self.playerView addSubview:(UIView *)player.view]; 
   
   //Start playback 
   [player play];
   ```
