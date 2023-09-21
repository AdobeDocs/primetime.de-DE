---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Benachrichtigungs-Listener.
title: Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Hinzufügen von Listenern für zeitgesteuerte Metadatenbenachrichtigungen {#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, implementieren Sie die entsprechenden Benachrichtigungs-Listener.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignisse warten, die Ihre Anwendung über zugehörige Aktivitäten informieren:

* `PTTimedMetadataChangedNotification`: Jedes Mal, wenn beim Analysieren des Inhalts ein eindeutiges abonniertes Tag identifiziert wird, bereitet TVSDK eine neue `PTTimedMetadata` -Objekt und sendet diese Benachrichtigung.

  Das Objekt enthält den Namen des Tags, für das Sie ein Abonnement abgeschlossen haben, die lokale Zeit in der Wiedergabe, in der dieses Tag angezeigt wird, und andere Daten.

* `PTMediaPlayerTimeChangeNotification` : Bei Live-/linearen Streams, bei denen das Manifest/die Wiedergabeliste regelmäßig aktualisiert wird, können zusätzliche benutzerdefinierte Tags in der aktualisierten Wiedergabeliste/dem aktualisierten Manifest angezeigt werden, sodass zusätzliche `TimedMetadata` -Objekte können zum `MediaPlayerItem.timedMetadata` -Eigenschaft.

  Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

  Rufen Sie die zeitgesteuerten Metadaten auf eine der folgenden Arten ab.

   * Legen Sie Ihre Anwendung fest, um sich selbst als Listener zum `PTTimedMetadataChangedNotification` Benachrichtigung erstellen und Objekt abrufen mithilfe von `PTTimedMetadataKey`.

     ```
     [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
       name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
     
     - (void) onTimedMetadataChanged:(NSNotification *) notification { 
         NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
         PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
     }
     ```

   * Zugriff auf `timedMetadataCollection` Eigenschaft von `PTMediaPlayerItem`, die aus allen `PTTimedMetadata` -Objekte, die bisher benachrichtigt wurden.
