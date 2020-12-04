---
description: PTNotification-Objekte bieten Informationen zu Änderungen im Player-Status, Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
seo-description: PTNotification-Objekte bieten Informationen zu Änderungen im Player-Status, Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.
seo-title: Benachrichtigungsinhalt
title: Benachrichtigungsinhalt
uuid: d42d2e89-1bdd-4be0-8a69-821fec6bbc75
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# Benachrichtigungen zu Player-Status, Aktivität, Fehlern und Protokollierung {#notifications-player-status-activity-errors-logging}

`PTNotification` Objekte enthalten Informationen zu Änderungen im Player-Status, Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Status des Players.

Ihre Anwendung kann die Benachrichtigungen und Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für die Diagnose und Überprüfung erstellen.

>[!NOTE]
>
>TVSDK verwendet auch *`notification`*-Benachrichtigungen, um auf `NSNotifications` ( `PTMediaPlayer`-Benachrichtigungen) *`event`*-Benachrichtigungen zu verweisen. Diese werden gesendet, um Informationen zur Player-Aktivität bereitzustellen.

TVSDK gibt auch `PTMediaPlayerNewNotificationItemEntryNotification` aus, wenn `PTNotification` ausgegeben wird.

Sie implementieren Ereignis-Listener, um Ereignis zu erfassen und darauf zu reagieren. In vielen Ereignissen werden Statusbenachrichtigungen für `PTNotification` bereitgestellt.

## Benachrichtigungsinhalt {#notification-content}

`PTNotification` enthält Informationen zum Status des Spielers.

TVSDK stellt eine chronologische Liste der `PTNotification`-Benachrichtigungen bereit. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * `type`: INFO, WARN oder FEHLER.
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Anmeldung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel/Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Beispielsweise stellt ein Schlüssel mit dem Namen `URL` einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf ein anderes  `PTNotification` Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen zur späteren Analyse lokal speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.

## Benachrichtigungseinrichtung {#notification-setup}

TVSDK richtet den Player für grundlegende Benachrichtigungen ein, obwohl Sie dasselbe Setup für benutzerdefinierte Benachrichtigungen durchführen müssen.

Es gibt zwei Implementierungen für `PTNotification`:

* Zum Zuhören
* So fügen Sie benutzerdefinierte Benachrichtigungen zu `PTNotificationHistory` hinzu

Zum Abhören von Benachrichtigungen instanziiert TVSDK die `PTNotification`-Klasse und hängt sie an eine Instanz von `PTMediaPlayerItem` an, die an eine PTMediaPlayer-Instanz angehängt ist. Es gibt nur eine `PTNotificationHistory` Instanz pro `PTMediaPlayer`.

>[!IMPORTANT]
>
>Wenn Sie Anpassungen hinzufügen, müssen Ihre Anwendungen und nicht TVSDK diese Schritte ausführen.

## Benachrichtigungen {#listen-to-notifications}

Es gibt zwei Möglichkeiten, die `PTNotification`-Benachrichtigung in `PTMediaPlayer` abzurufen:

1. Überprüfen Sie manuell die `PTNotificationHistory` des `PTMediaPlayerItem` mit einem Timer und überprüfen Sie die Unterschiede:

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Verwenden Sie die gepostete [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) von `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Registrieren Sie sich beim `NSNotification`, indem Sie die Instanz des `PTMediaPlayer` verwenden, von der Sie Benachrichtigungen erhalten möchten:

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Implementieren von Benachrichtigungs-Rückrufen {#implement-notification-callbacks}

Sie können Benachrichtigungsrückrufe implementieren.

Implementieren Sie den Benachrichtigungsrückruf, indem Sie `PTNotification` aus den `NSNotification`-Benutzerinformationen abrufen und die zugehörigen Werte mit `PTMediaPlayerNotificationKey` lesen:

```
- (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
    PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
    NSLog(@"Notification: %@", notification); 
}
```

## hinzufügen benutzerspezifische Benachrichtigungen {#add-custom-notifications}

So fügen Sie eine benutzerdefinierte Benachrichtigung hinzu:
Erstellen Sie ein neues `PTNotification` und fügen Sie es dem `PTNotificationHistory` hinzu, indem Sie das aktuelle `PTMediaPlayerItem` verwenden:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
