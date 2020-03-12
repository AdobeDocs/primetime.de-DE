---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, überwachen Sie AdobePSDK.TimedMetadataEvent.
seo-description: Um Benachrichtigungen über Tags im Manifest zu erhalten, überwachen Sie AdobePSDK.TimedMetadataEvent.
seo-title: Hinzufügen Listener für Benachrichtigungen über zeitgesteuerte Metadaten
title: Hinzufügen Listener für Benachrichtigungen über zeitgesteuerte Metadaten
uuid: c82c5549-0ab6-4343-a766-5176e784d4cb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Hinzufügen Listener für Benachrichtigungen über zeitgesteuerte Metadaten{#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, überwachen Sie AdobePSDK.TimedMetadataEvent.

Wenn ein neues `TimedMetadata` Objekt erstellt wird, löst der MediaPlayer `AdobePSDK.TimedMetadataEvent`aus.

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

ID3-Metadaten werden durch dasselbe `Events.TimedMetadataEvent`gesendet. Mit der `timedMetadata.type` Eigenschaft können Sie zwischen TAG und ID3 unterscheiden.

