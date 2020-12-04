---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Ereignis-Listener.
seo-description: Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Ereignis-Listener.
seo-title: hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
title: hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
uuid: cd7a5936-d63a-4711-ac16-2d79bac099a3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# hinzufügen Listener für zeitgesteuerte Metadatenbenachrichtigungen {#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Ereignis-Listener.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignis achten, die Ihre Anwendung über die zugehörige Aktivität informieren:

* `onTimedMetadata`: Jedes Mal, wenn während der Analyse des Inhalts ein eindeutiges abonniertes Tag identifiziert wird, bereitet TVSDK ein neues  `TimedMetadata` Objekt vor und löst dieses Ereignis aus.

   Das Objekt enthält den Namen des Tags, für das Sie ein Abonnement abgeschlossen haben, die lokale Zeit in der Wiedergabe, in der dieses Tag angezeigt wird, und andere Daten.

   Hör auf Ereignisse!

   ```java
   private final TimedMetadataEventListener timedMetadataEventListener =  
     new TimedMetadataEventListener() { 
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
           } else if (_mediaPlayer.getPlaybackRange() !=  
                      null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
               displayRanges(); 
           } 
       } 
   }; 
   ```

ID3-Metadaten verwenden denselben onTimedMetadata-Listener, um das Vorhandensein eines ID3-Tags anzugeben. Dies sollte jedoch keine Verwirrung stiften, da Sie die `type`-Eigenschaft eines `TimedMetadata`-Objekts verwenden können, um zwischen TAG und ID3 zu unterscheiden. Weitere Informationen zu ID3-Tags finden Sie unter [ID3-Tags](../../../tvsdk-1.4-for-android/notification-system/android-1.4-id3-metadata-retrieve.md).
