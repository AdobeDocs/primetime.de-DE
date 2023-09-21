---
description: Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabezeit mit der Startzeit übereinstimmt.
title: Zeitgesteuerte Metadaten verwenden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Zeitgesteuerte Metadaten verwenden {#use-timed-metadata}

Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabezeit mit der Startzeit übereinstimmt.

So verwenden Sie diese gespeicherten `PTTimedMetadata` Objekte während der Wiedergabe verwenden Sie das gespeicherte Wörterbuch aus [Speichern von zeitgesteuerten Metadatenobjekten beim Versand](../../../tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-custom-tags-configure/ios-3x-timed-metadata-store.md).

1. Extrahieren und aktualisieren Sie die aktuelle Wiedergabedauer aus dieser Benachrichtigung und suchen Sie alle `PTTimedMetadata` -Objekte mit Startzeiten, die der aktuellen Wiedergabedauer entsprechen.

   Sie können diese Objekte verwenden, um verschiedene Aktionen durchzuführen.

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

1. Periodisches Leeren veraltet `PTTimedMetadata` -Instanzen aus der Liste, um zu verhindern, dass der Speicher ständig wächst.
