---
description: Sie können Ihr eigenes Protokollierungssystem implementieren.
seo-description: Sie können Ihr eigenes Protokollierungssystem implementieren.
seo-title: Benutzerdefinierte Protokollierung
title: Benutzerdefinierte Protokollierung
uuid: f056d7d7-ec3a-4cf1-997f-72a89bbc9447
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Benutzerdefinierte Protokollierung {#customized-logging}

Sie können Ihr eigenes Protokollierungssystem implementieren.

Zusätzlich zur Protokollierung mithilfe vordefinierter Benachrichtigungen können Sie ein Protokollierungssystem implementieren, das Ihre Protokollmeldungen und Nachrichten verwendet, die von TVSDK generiert werden. Weitere Informationen zu vordefinierten Benachrichtigungen finden Sie unter [Das Benachrichtigungssystem](https://help.adobe.com/en_US/primetime/psdk/ios/index.html#PSDKs-concept-The_Notification_System). Sie können diese Protokolle verwenden, um Fehler in Ihren Player-Anwendungen zu beheben und einen besseren Einblick in den Wiedergabe- und Werbeablauf zu erhalten.

Die benutzerdefinierte Protokollierung verwendet eine freigegebene Singleton-Instanz der `PSDKPTLogFactory`, die eine Möglichkeit zum Protokollieren von Nachrichten an mehrere Protokollfunktionen bietet. Sie definieren und fügen (registrieren) einen oder mehrere Protokollen zum `PTLogFactory`. Auf diese Weise können Sie mehrere Protokollfunktionen mit benutzerdefinierten Implementierungen definieren, z. B. eine Konsolenprotokollierung, eine Webprotokollierung oder eine Protokollfunktion für den Konsolenverlauf.

TVSDK erzeugt Logmeldungen für viele seiner Aktivitäten, die an alle registrierten Logger `PTLogFactory` weitergeleitet werden. Ihre Anwendung kann auch benutzerdefinierte Protokollmeldungen generieren, die an alle registrierten Anmelder weitergeleitet werden. Jede Protokollfunktion kann die Nachrichten filtern und entsprechende Maßnahmen ergreifen.

Es gibt zwei Implementierungen für `PTLogFactory`:

* Zum Listening von Protokollen.
* Zum Hinzufügen von Protokollen zu einer `PTLogFactory`.

## Protokolle abrufen {#listen-to-logs}

So registrieren Sie sich zum Listening von Protokollen:
1. Implementieren Sie eine benutzerdefinierte Klasse, die dem Protokoll folgt `PTLogger`:

   ```
   @implementation PTConsoleLogger 
   
   + (PTConsoleLogger *) consoleLogger { 
       return [[[PTConsoleLogger alloc] init] autorelease]; 
   } 
   
   - (void)logEntry:(PTLogEntry *)entry { 
       //Log the message to the console using NSLog  
       NSLog(@"[%@] %@", entry.tag, entry.message); 
   } 
   
   @end
   ```

1. Um die Instanz für den Empfang von Protokolleinträgen zu registrieren, fügen Sie eine Instanz der `PTLogger` der hinzu `PTLoggerFactory`:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

Hier ein Beispiel für das Filtern von Protokollen anhand des `PTLogEntry` Typs:

```
@implementation PTConsoleLogger 
 
+ (PTConsoleLogger *) consoleLogger { 
    return [[[PTConsoleLogger alloc] init] autorelease]; 
} 
 
- (id) init { 
    self = [super init]; 
 
    if (self) { 
        self.logLevel = PTLogEntryTypeInfo; 
    } 
 
    return self; 
} 
 
- (void)logEntry:(PTLogEntry *) entry { 
    //Filtering the entry by log level  
    if (entry.type < _logLevel) { 
        return; 
    } 
 
    //Log the message to the console using NSLog NSLog(@"[%@] %@", entry.tag, entry.message); 
} 
 
@end
```

## Hinzufügen neue Protokollmeldungen {#add-new-log-messages}

So registrieren Sie sich zum Abhören von Protokollen:

Erstellen Sie eine neue `PTLogEntry` und fügen Sie sie hinzu `thePTLogFactory`:

Sie können eine Instanz manuell instanziieren `PTLogEntry` und der `PTLogFactory` freigegebenen Instanz hinzufügen oder eine der Makros verwenden, um dieselbe Aufgabe auszuführen.

Hier ein Beispiel für die Protokollierung mit dem `PTLogDebug` Makro:

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
