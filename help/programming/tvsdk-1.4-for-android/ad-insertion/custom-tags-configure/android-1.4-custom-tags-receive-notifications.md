---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Ereignis-Listener.
title: Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen {#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Ereignis-Listener.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignisse warten, die Ihre Anwendung über zugehörige Aktivitäten informieren:

* `onTimedMetadata`: Jedes Mal, wenn beim Analysieren des Inhalts ein eindeutiges abonniertes Tag identifiziert wird, bereitet TVSDK eine neue `TimedMetadata` -Objekt und sendet dieses Ereignis.

  Das Objekt enthält den Namen des Tags, für das Sie ein Abonnement abgeschlossen haben, die lokale Zeit in der Wiedergabe, in der dieses Tag angezeigt wird, und andere Daten.

  Suchen Sie nach Ereignissen.

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

ID3-Metadaten verwenden denselben onTimedMetadata-Listener, um das Vorhandensein eines ID3-Tags anzugeben. Dies sollte jedoch nicht zu Verwirrung führen, da Sie eine `TimedMetadata` -Objekt `type` -Eigenschaft, um zwischen TAG und ID3 zu unterscheiden. Weitere Informationen zu ID3-Tags finden Sie unter [ID3-Tags](../../../tvsdk-1.4-for-android/notification-system/android-1.4-id3-metadata-retrieve.md).
