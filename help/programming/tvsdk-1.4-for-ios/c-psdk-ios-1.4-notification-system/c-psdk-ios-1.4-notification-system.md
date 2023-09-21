---
description: PTNotification-Objekte bieten Informationen zu Änderungen des Player-Status, Warnungen und Fehler. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
title: Benachrichtigungen bezüglich Player-Status, -Aktivität, Fehler und Protokollen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Benachrichtigungen bezüglich Player-Status, Aktivität, Fehler und Protokollierung  {#notifications-for-player-status-activity-errors-and-logs-overview}

PTNotification-Objekte bieten Informationen zu Änderungen des Player-Status, Warnungen und Fehler. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.

Ihre Anwendung kann die Benachrichtigung und Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für Diagnose und Validierung erstellen.

>[!IMPORTANT]
>
>TVSDK verwendet auch *`notification`* verweisen auf `NSNotifications` ( `PTMediaPlayer` Benachrichtigungen) *`event`* Benachrichtigungen, die gesendet werden, um Informationen zur Player-Aktivität bereitzustellen.

TVSDK-Probleme `PTMediaPlayerNewNotificationItemEntryNotification` wenn Probleme auftreten `PTNotification`.

Sie implementieren Ereignis-Listener, um Ereignisse zu erfassen und darauf zu reagieren. Viele Ereignisse bieten `PTNotification` Statusbenachrichtigungen.

## Benachrichtigungsinhalt {#notification-content}

Die PTNotification liefert Informationen, die sich auf den Status des Players beziehen.

TVSDK bietet eine chronologische Liste von `PTNotification` Benachrichtigungen. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * `type`: INFO, WARN oder FEHLER.
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Benachrichtigung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel-Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Beispiel: ein Schlüssel mit dem Namen `URL` stellt einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf einen anderen `PTNotification` -Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen lokal zur späteren Analyse speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.

## Benachrichtigungseinstellungen {#notification-setup}

TVSDK richtet den Player für grundlegende Benachrichtigungen ein. Sie müssen jedoch dieselbe Einrichtung für benutzerdefinierte Benachrichtigungen durchführen.

Es gibt zwei Implementierungen für `PTNotification`:

* Zu lauschen
* Hinzufügen benutzerdefinierter Benachrichtigungen zu `PTNotificationHistory`

Um Benachrichtigungen zu überwachen, instanziiert TVSDK die `PTNotification` -Klasse und hängt sie an eine Instanz der `PTMediaPlayerItem`, das an eine PTMediaPlayer-Instanz angehängt ist. Es gibt nur einen `PTNotificationHistory` Instanz pro `PTMediaPlayer`.

>[!IMPORTANT]
>
>Wenn Sie Anpassungen hinzufügen, müssen Ihre Anwendungen und nicht TVSDK diese Schritte ausführen.

## Benachrichtigungen abrufen {#listen-to-notifications}

Es gibt zwei Möglichkeiten, die `PTNotification` Benachrichtigung im `PTMediaPlayer`:

1. Manuelles Überprüfen der `PTNotificationHistory` des `PTMediaPlayerItem` mit einem Timer und überprüfen Sie die Unterschiede:

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Posting verwenden [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) des `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Registrieren Sie sich bei `NSNotification` durch Verwendung der -Instanz der `PTMediaPlayer` von dem aus Sie Benachrichtigungen erhalten möchten:

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Implementieren von Benachrichtigungs-Rückrufen {#implement-notification-callbacks}

Sie können Benachrichtigungs-Rückrufe implementieren.

1. Implementieren Sie den Benachrichtigungs-Callback, indem Sie die `PTNotification` aus dem `NSNotification` Benutzerinformationen und Lesen der Werte mithilfe von `PTMediaPlayerNotificationKey`:

   ```
   - (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
       PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
       NSLog(@"Notification: %@", notification); 
   }
   ```

## Hinzufügen benutzerdefinierter Benachrichtigungen {#add-custom-notifications}

So fügen Sie eine benutzerdefinierte Benachrichtigung hinzu: Erstellen Sie eine neue `PTNotification` und fügen Sie sie zum `PTNotificationHistory` durch Verwendung des aktuellen `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
