---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.
title: Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen{#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, registrieren Sie die entsprechenden Ereignis-Listener.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignisse warten, die Ihre Anwendung über zugehörige Aktivitäten informieren:

* `MediaPlayerItemEvent.ITEM_CREATED`: Die erste Liste von `TimedMetadata` -Objekte sind verfügbar, nachdem `MediaPlayerItem` erstellt wird.

  Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Bei Live-/linearen Streams, bei denen das Manifest/die Wiedergabeliste regelmäßig aktualisiert wird, können zusätzliche benutzerdefinierte Tags in der aktualisierten Wiedergabeliste/dem aktualisierten Manifest angezeigt werden, sodass zusätzliche `TimedMetadata` -Objekte können zum `MediaPlayerItem.timedMetadata` -Eigenschaft.

  Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Jedes Mal, wenn ein neuer `TimedMetadata` -Objekt erstellt wurde, wird dieses Ereignis vom MediaPlayer ausgelöst.

  Dieses Ereignis wird nicht für die `TimedMetadata` -Objekt, das während der Initialisierungsphase erstellt wurde.

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

ID3-Metadaten werden über denselben `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`. Dies sollte jedoch nicht zu Verwirrung führen, da Sie die Funktion `type` -Eigenschaft, um zwischen TAG und ID3 zu unterscheiden. Weitere Informationen zu ID3-Tags finden Sie unter [ID3-Tags](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md).
