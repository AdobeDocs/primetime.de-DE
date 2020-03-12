---
description: 'null'
seo-description: 'null'
seo-title: Markierbereiche
title: Markierbereiche
uuid: ca544f64-ef83-4c08-8ec5-1bc07fdba3c4
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d

---


# Anwendungsfälle zum Löschen und Ersetzen von Anzeigen {#use-cases-delete-replace-ads}

Im Folgenden finden Sie Anwendungsfälle zum Löschen und Ersetzen von Anzeigen:

## Markierbereiche {#mark-ranges}

So implementieren Sie die Inhaltsbereiche `PTTimeRangeCollection` und Markieren als Anzeigen:
1. Bereiten Sie das `PTTimeRangeCollection`vor.
1. Legen Sie den Typ der `PTTimeRangeCollection` auf `PTTimeRangeCollectionTypeMarkRanges`fest.

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

1. Erstellen Sie die `PTAdMetadata` und legen Sie die `PTTimeRangeCollection`.

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

## Ersetzen von Bereichen {#replace-ranges}

So implementieren Sie Inhaltsbereiche `PTTimeRangeCollection` und löschen sie als Anzeigen:
1. Bereiten Sie sich vor `PTTimeRangeCollection`.
1. Legen Sie den Typ der `PTTimeRangeCollection` auf `PTTimeRangeCollectionTypeReplaceRanges`fest.

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
   >Das Argument `replacementDuration` ist optional. Wenn sie nicht definiert ist, `AdServer` bestimmt die Variable die Dauer der Werbeunterbrechung.

1. Erstellen Sie die `PTAdMetadata` und legen Sie die `PTTimeRangeCollection`.

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
   >Obwohl der `signalingMode` Wert auf `PTAdSignalingModeCustomRanges`festgelegt ist, wird dieser Anzeigensignalisierungsmodus automatisch eingestellt, wenn die Einstellung `PTTimeRangeCollection` des Typs festgelegt wird `PTTimeRangeCollectionTypeReplace`.

1. Erstellen Sie die Wiedergabe des Players und Beginns.

   ```
   //Create PTMediaPlayer using the created PTMediaPlayer 
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:playerItem]; 
   
   //Add player to the player UIView 
   [self.playerView addSubview:(UIView *)player.view]; 
   
   //Start playback 
   [player play];
   ```

## Bereiche löschen {#delete-ranges}

So implementieren Sie Inhaltsbereiche `PTTimeRangeCollection` und löschen sie als Anzeigen:
1. Bereiten Sie das `PTTimeRangeCollection`vor.
1. Legen Sie den Typ des `PTTimeRangeCollection` auf `PTTimeRangeCollectionTypeDeleteRanges`, der TVSDK benachrichtigt, dass die bereitgestellten Bereiche gelöscht werden müssen.

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

1. Erstellen Sie die `PTAdMetadata` und legen Sie die `PTTimeRangeCollection`.

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
   >Das Einfügen von Anzeigen erfolgt, nachdem die benutzerdefinierten Bereiche basierend auf dem `PTAdMetadata` und dem aktuellen Bereich gelöscht wurden `PTAdSignalingMode`.

1. Erstellen Sie die Wiedergabe des Players und Beginns.

   ```
   //Create PTMediaPlayer using the created PTMediaPlayer 
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:playerItem]; 
   
   //Add player to the player UIView 
   [self.playerView addSubview:(UIView *)player.view]; 
   
   //Start playback 
   [player play];
   ```
