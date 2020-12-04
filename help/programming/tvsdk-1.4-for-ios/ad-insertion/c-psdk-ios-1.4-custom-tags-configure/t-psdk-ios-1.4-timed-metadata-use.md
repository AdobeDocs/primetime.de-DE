---
description: Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabedauer mit der Beginn-Zeit übereinstimmt.
seo-description: Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabedauer mit der Beginn-Zeit übereinstimmt.
seo-title: Verwenden von Zeitmetadaten
title: Verwenden von Zeitmetadaten
uuid: 9bbdaefa-4ac5-4e08-92b4-15ebe5c46864
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# Verwenden Sie zeitgesteuerte Metadaten{#use-timed-metadata}

Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabedauer mit der Beginn-Zeit übereinstimmt.

Um diese gespeicherten `PTTimedMetadata`-Objekte während der Wiedergabe zu verwenden, verwenden Sie das gespeicherte Wörterbuch von [Zeitmetadatenobjekte speichern, während sie gesendet werden.](../../../tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-timed-metadata-store.md)

1. Extrahieren und aktualisieren Sie die aktuelle Wiedergabezeit aus dieser Benachrichtigung und suchen Sie alle `PTTimedMetadata`-Objekte mit Beginn-Zeiten, die der aktuellen Wiedergabezeit entsprechen.

   Mit diesen Objekten können Sie verschiedene Aktionen ausführen.

   Beispiel:

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification 
   { 
       CMTimeRange seekableRange = self.player.seekableRange; 
       if (CMTIMERANGE_IS_VALID(seekableRange)) 
       { 
           int currentTime = (int) CMTimeGetSeconds(self.player.currentTime); 
           NSArray *allKeys = timedMetadataCollection ? [timedMetadataCollection allKeys] : [NSArray array]; 
           NSMutableArray *timedMetadatasToDelete = [[[NSMutableArray alloc] init] autorelease]; 
           int count = [allKeys count]; 
   
           for (int i=count - 1; i > -1; i--) 
           { 
              NSNumber *currTimedMetadataTime = allKeys[i]; 
              if ([currTimedMetadataTime integerValue] == currentTime) 
              { 
               /* 
                   Use the timed metadata here and remove it from the collection. 
               */ 
                NSLog (@"IN PLAYBACK TIME %i TO EXECUTE TIMEDMETADATA %@ scheduled at time %f",currentTime,currTimedMetadata.name,CMTimeGetSeconds(currTimedMetadata.time)); 
   
               PTTimedMetadata *currTimedMetadata = [timedMetadataCollection objectForKey:currTimedMetadataTime]; 
               [timedMetadatasToDelete addObject:currTimedMetadataTime]; 
              } 
           } 
   
           for (int i=0; i<[timedMetadatasToDelete count]; i++) 
           { 
               NSNumber *timedMetadataToDelete = timedMetadatasToDelete[i]; 
               [timedMetadataCollection removeObjectForKey:timedMetadataToDelete]; 
           } 
       } 
   }
   ```

1. Regelmäßig die statische `PTTimedMetadata`-Instanzen aus der Liste entfernen, um zu verhindern, dass der Speicher ständig wächst.
