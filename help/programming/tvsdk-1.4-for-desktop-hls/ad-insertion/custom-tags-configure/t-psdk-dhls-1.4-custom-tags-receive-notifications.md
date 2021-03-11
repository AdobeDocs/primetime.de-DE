---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.
title: hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen{#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignis achten, die Ihre Anwendung über die zugehörige Aktivität informieren:

* `MediaPlayerItemEvent.ITEM_CREATED`: Die anfängliche Liste von  `TimedMetadata` Objekten ist verfügbar, nachdem die erstellt  `MediaPlayerItem` wurde.

   Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Bei Live-/linearen Streams, bei denen die Manifest-/Wiedergabeliste regelmäßig aktualisiert wird, können in der aktualisierten Wiedergabeliste/dem Manifest zusätzliche benutzerdefinierte Tags angezeigt werden, sodass zusätzliche  `TimedMetadata` Objekte zur  `MediaPlayerItem.timedMetadata` Eigenschaft hinzugefügt werden können.

   Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Jedes Mal, wenn ein neues  `TimedMetadata` Objekt erstellt wird, wird dieses Ereignis vom MediaPlayer ausgelöst.

   Dieses Ereignis wird nicht für das `TimedMetadata`-Objekt ausgelöst, das während der Initialisierungsphase erstellt wurde.

1. Implementieren Sie die entsprechenden Listener.

   ```
   private function onItemCreated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onItemUpdated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onTimedMetadataAvailable(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       // process timed metadata 
   }
   ```

1. Registrieren Sie die Ereignis-Listener.

   ```
   player.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
   player.addEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE,  
                           onTimedMetadataAvailable);
   ```

ID3-Metadaten werden über dasselbe `TimedMetadataEvent.TIMED_METADATA_AVAILABLE` gesendet. Dies sollte jedoch keine Verwirrung stiften, da Sie die `type`-Eigenschaft eines TimedMetadata-Objekts verwenden können, um zwischen TAG und ID3 zu unterscheiden. Weitere Informationen zu ID3-Tags finden Sie unter [ID3-Tags](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md).