---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, überwachen Sie AdobePSDK.TimedMetadataEvent.
title: hinzufügen Listener für Benachrichtigungen über zeitgesteuerte Metadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---


# hinzufügen Listener für Benachrichtigungen über zeitgesteuerte Metadaten{#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, überwachen Sie AdobePSDK.TimedMetadataEvent.

Wenn ein neues `TimedMetadata`-Objekt erstellt wird, löst der MediaPlayer `AdobePSDK.TimedMetadataEvent` aus.

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

ID3-Metadaten werden über dasselbe `Events.TimedMetadataEvent` gesendet. Mit der Eigenschaft `timedMetadata.type` können Sie zwischen TAG und ID3 unterscheiden.

