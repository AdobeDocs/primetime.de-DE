---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.
seo-description: Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.
seo-title: Hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
title: Hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
uuid: 336882e7-e2d8-49b8-a23d-f236c7e6a594
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen {#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf `onTimedMetadata`die entsprechenden Aktivitäten achten. Jedes Mal, wenn während der Analyse des Inhalts ein eindeutiges abonniertes Tag identifiziert wird, bereitet TVSDK ein neues `TimedMetadata` Objekt vor und löst dieses Ereignis aus. Das Objekt enthält den Namen des Tags, für das Sie ein Abonnement abgeschlossen haben, die lokale Zeit in der Wiedergabe, in der dieses Tag angezeigt wird, und andere Daten.

1. Hör auf Ereignisse!

   ```java
   private final TimedMetadataEventListener timedMetadataEventListener = new TimedMetadataEventListener() { 
       @Override 
       public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { 
           TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata(); 
   
           TimedMetadata.Type type = timedMetadata.getType(); 
           if (type.equals(TimedMetadata.Type.ID3)){ 
               Metadata metadata = timedMetadata.getMetadata(); 
               Set<String> keys = metadata.keySet(); 
               for (String key : keys) { 
                   String value = metadata.getValue(key); 
               } 
           } else if (_mediaPlayer.getPlaybackRange() != null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
               displayRanges(); 
           } 
       } 
   }; 
   ```

ID3-Metadaten verwenden denselben `onTimedMetadata` Listener, um das Vorhandensein eines ID3-Tags anzugeben. Dies sollte jedoch keine Verwirrung stiften, da Sie mit der `TimedMetadata``type` Eigenschaft zwischen TAG und ID3 unterscheiden können. Weitere Informationen zu ID3-Tags finden Sie unter [ID3-Tags](../../content-playback-options/t-psdk-android-2.7-id3-metadata-retrieve.md).