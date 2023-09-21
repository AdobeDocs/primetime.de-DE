---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, überwachen Sie AdobePSDK.TimedMetadataEvent.
title: Hinzufügen von Listenern für Benachrichtigungen mit zeitgesteuerten Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# Hinzufügen von Listenern für Benachrichtigungen mit zeitgesteuerten Metadaten{#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, überwachen Sie AdobePSDK.TimedMetadataEvent.

Wenn ein neuer `TimedMetadata` -Objekt erstellt wird, sendet der MediaPlayer `AdobePSDK.TimedMetadataEvent`.

1. Implementieren Sie die entsprechenden Listener.

   ```js
   function onTimedMetadataEvent(event) { 
       var timedMetadata = event.timedMetadata; 
       // process the timed metadata collection 
       } 
   ```

1. Registrieren Sie die Ereignis-Listener.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE, onTimedMetadataEvent);
   ```

ID3-Metadaten werden über denselben `Events.TimedMetadataEvent`. Sie können die `timedMetadata.type` -Eigenschaft, um zwischen TAG und ID3 zu unterscheiden.
