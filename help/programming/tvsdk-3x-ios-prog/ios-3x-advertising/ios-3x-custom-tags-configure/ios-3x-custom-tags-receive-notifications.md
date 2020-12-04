---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Benachrichtigungs-Listener.
seo-description: Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Benachrichtigungs-Listener.
seo-title: hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
title: hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
uuid: b6939011-a6ff-4342-8e7c-3a0c805ee91c
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# hinzufügen Listener für zeitgesteuerte Metadatenbenachrichtigungen {#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Benachrichtigungs-Listener.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignis achten, die Ihre Anwendung über die zugehörige Aktivität informieren:

* `PTTimedMetadataChangedNotification`: Jedes Mal, wenn während der Analyse des Inhalts ein eindeutiges abonniertes Tag identifiziert wird, bereitet TVSDK ein neues  `PTTimedMetadata` Objekt vor und löst diese Benachrichtigung aus.

   Das Objekt enthält den Namen des Tags, für das Sie ein Abonnement abgeschlossen haben, die lokale Zeit in der Wiedergabe, in der dieses Tag angezeigt wird, und andere Daten.

* `PTMediaPlayerTimeChangeNotification` : Bei Live-/linearen Streams, bei denen die Manifest-/Wiedergabeliste regelmäßig aktualisiert wird, können in der aktualisierten Wiedergabeliste/dem Manifest zusätzliche benutzerdefinierte Tags angezeigt werden, sodass zusätzliche  `TimedMetadata` Objekte zur  `MediaPlayerItem.timedMetadata` Eigenschaft hinzugefügt werden können.

   Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

   Rufen Sie die Metadaten mit Timed auf eine der folgenden Weisen ab.

   * Legen Sie Ihre Anwendung so fest, dass sie sich als Listener der `PTTimedMetadataChangedNotification`-Benachrichtigung hinzufügt und das Objekt mit `PTTimedMetadataKey` abruft.

      ```
      [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
        name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
      
      - (void) onTimedMetadataChanged:(NSNotification *) notification { 
          NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
          PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
      }
      ```

   * Greifen Sie auf die Eigenschaft `timedMetadataCollection` von `PTMediaPlayerItem` zu, die aus allen `PTTimedMetadata`-Objekten besteht, die bisher benachrichtigt wurden.