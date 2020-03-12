---
description: Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabezeit mit der Beginn-Zeit übereinstimmt.
seo-description: Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabezeit mit der Beginn-Zeit übereinstimmt.
seo-title: Verwenden von Zeitmetadaten
title: Verwenden von Zeitmetadaten
uuid: 1531780f-2502-4235-818c-6c0a6bf3d348
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Verwenden von Zeitmetadaten {#use-timed-metadata}

Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabezeit mit der Beginn-Zeit übereinstimmt.

Um diese gespeicherten `PTTimedMetadata` Objekte während der Wiedergabe zu verwenden, verwenden Sie das gespeicherte Wörterbuch aus Zeitmetadatenobjekten im [Store, während sie ausgelöst](../../../tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-custom-tags-configure/ios-3x-timed-metadata-store.md)werden.

1. Extrahieren und aktualisieren Sie die aktuelle Wiedergabezeit aus dieser Benachrichtigung und suchen Sie alle `PTTimedMetadata` Objekte mit Beginn, die der aktuellen Wiedergabezeit entsprechen.

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

1. Passen Sie regelmäßig statische `PTTimedMetadata` Instanzen von der Liste ab, um zu verhindern, dass der Speicher ständig wächst.