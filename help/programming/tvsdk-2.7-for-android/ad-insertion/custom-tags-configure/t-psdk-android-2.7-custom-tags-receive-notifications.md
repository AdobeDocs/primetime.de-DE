---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.
title: Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen {#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf `onTimedMetadata`, die Ihre Anwendung über zugehörige Aktivitäten informieren. Jedes Mal, wenn beim Analysieren des Inhalts ein eindeutiges abonniertes Tag identifiziert wird, bereitet TVSDK eine neue `TimedMetadata` -Objekt und sendet dieses Ereignis. Das Objekt enthält den Namen des Tags, für das Sie ein Abonnement abgeschlossen haben, die lokale Zeit in der Wiedergabe, in der dieses Tag angezeigt wird, und andere Daten.

1. Suchen Sie nach Ereignissen.

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

ID3-Metadaten verwenden die gleiche `onTimedMetadata` Listener, um das Vorhandensein eines ID3-Tags anzugeben. Dies sollte jedoch nicht zu Verwirrung führen, da Sie die `TimedMetadata` `type` -Eigenschaft, um zwischen TAG und ID3 zu unterscheiden. Weitere Informationen zu ID3-Tags finden Sie unter  [ID3-Tags](../../content-playback-options/t-psdk-android-2.7-id3-metadata-retrieve.md).
