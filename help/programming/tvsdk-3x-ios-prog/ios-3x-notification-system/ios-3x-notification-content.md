---
description: PTNotification-Objekte bieten Informationen zu Änderungen im Player-Status, Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
seo-description: PTNotification-Objekte bieten Informationen zu Änderungen im Player-Status, Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
seo-title: Benachrichtigungsinhalt
title: Benachrichtigungsinhalt
uuid: d42d2e89-1bdd-4be0-8a69-821fec6bbc75
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Benachrichtigungen über Player-Status, Aktivität, Fehler und Protokollierung {#notifications-player-status-activity-errors-logging}

`PTNotification` Objekte enthalten Informationen zu Änderungen im Player-Status, Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.

Ihre Anwendung kann die Benachrichtigungen und Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für die Diagnose und Überprüfung erstellen.

>[!NOTE]
>
>TVSDK verwendet auch *`notification`* den Verweis auf `NSNotifications` ( `PTMediaPlayer` Benachrichtigungen) *`event`* -Benachrichtigungen, die zur Bereitstellung von Informationen zur Player-Aktivität gesendet werden.

TVSDK gibt auch Probleme `PTMediaPlayerNewNotificationItemEntryNotification` bei der Ausgabe `PTNotification`.

Sie implementieren Ereignis-Listener, um Ereignis zu erfassen und darauf zu reagieren. In vielen Ereignissen werden `PTNotification` Statusbenachrichtigungen bereitgestellt.

## Benachrichtigungsinhalt {#notification-content}

`PTNotification` enthält Informationen zum Status des Spielers.

TVSDK stellt eine chronologische Liste der `PTNotification` Benachrichtigungen bereit. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * `type`: INFO, WARN oder FEHLER.
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Anmeldung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel/Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Ein Schlüssel mit dem Namen `URL` stellt beispielsweise einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf ein anderes `PTNotification` Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen zur späteren Analyse lokal speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.

## Benachrichtigungseinrichtung {#notification-setup}

TVSDK richtet den Player für grundlegende Benachrichtigungen ein, obwohl Sie dasselbe Setup für benutzerdefinierte Benachrichtigungen durchführen müssen.

Es gibt zwei Implementierungen für `PTNotification`:

* Zum Zuhören
* So fügen Sie benutzerdefinierte Benachrichtigungen hinzu `PTNotificationHistory`

Zum Abhören von Benachrichtigungen instanziiert TVSDK die `PTNotification` Klasse und hängt sie an eine Instanz der Instanz an, die an eine PTMediaPlayer-Instanz angehängt `PTMediaPlayerItem`ist. Es gibt nur eine `PTNotificationHistory` Instanz pro `PTMediaPlayer`.

>[!IMPORTANT]
>
>Wenn Sie Anpassungen hinzufügen, müssen Ihre Anwendungen und nicht TVSDK diese Schritte ausführen.

## Benachrichtigungen abrufen {#listen-to-notifications}

Es gibt zwei Möglichkeiten, die `PTNotification` Benachrichtigung im `PTMediaPlayer`abzuhören:

1. Überprüfen Sie manuell die `PTNotificationHistory` Anzeige des `PTMediaPlayerItem` Timers und prüfen Sie die Unterschiede:

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Verwenden Sie die gepostete [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) der `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Registrieren Sie sich bei der `NSNotification` Instanz der Instanz, von der Sie Benachrichtigungen abrufen `PTMediaPlayer` möchten:

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Implementieren von Benachrichtigungs-Rückrufen {#implement-notification-callbacks}

Sie können Benachrichtigungsrückrufe implementieren.

Implementieren Sie den Benachrichtigungsrückruf, indem Sie die `PTNotification` Informationen aus den `NSNotification` Benutzerinformationen abrufen und die Werte mithilfe `PTMediaPlayerNotificationKey`folgender Elemente lesen:

```
- (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
    PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
    NSLog(@"Notification: %@", notification); 
}
```

## Hinzufügen von benutzerdefinierten Benachrichtigungen {#add-custom-notifications}

So fügen Sie eine benutzerdefinierte Benachrichtigung hinzu:
Erstellen Sie eine neue `PTNotification` und fügen Sie sie der `PTNotificationHistory` mithilfe der aktuellen Version hinzu `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
