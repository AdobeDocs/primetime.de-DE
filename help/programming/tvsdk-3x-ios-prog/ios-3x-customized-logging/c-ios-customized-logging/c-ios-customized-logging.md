---
description: Sie können Ihr eigenes Protokollierungssystem implementieren.
title: Grundlegendes zur benutzerdefinierten Protokollierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Benutzerdefinierte Protokollierung {#customized-logging}

Sie können Ihr eigenes Protokollierungssystem implementieren.

Zusätzlich zur Protokollierung mithilfe vordefinierter Benachrichtigungen können Sie ein Protokollierungssystem implementieren, das Ihre Protokollmeldungen und von TVSDK generierten Nachrichten verwendet. Weitere Informationen zu vordefinierten Benachrichtigungen finden Sie unter [Das Benachrichtigungssystem](https://help.adobe.com/en_US/primetime/psdk/ios/index.html#PSDKs-concept-The_Notification_System). Sie können diese Protokolle verwenden, um Fehler in Player-Anwendungen zu beheben und ein besseres Verständnis des Wiedergabe- und Werbe-Workflows zu erhalten.

Die benutzerdefinierte Protokollierung verwendet eine freigegebene Singleton-Instanz der `PSDKPTLogFactory`, die einen Mechanismus zur Protokollierung von Nachrichten an mehrere Logger bietet. Sie definieren und fügen einen oder mehrere Logger zum `PTLogFactory`. Auf diese Weise können Sie mehrere Logger mit benutzerdefinierten Implementierungen definieren, z. B. eine Konsolenprotokollierung, eine Webprotokollierung oder eine Protokollfunktion für den Konsolenverlauf.

TVSDK generiert Protokollmeldungen für viele seiner Aktivitäten, die die `PTLogFactory` Weiterleitung an alle registrierten Logger. Ihre Anwendung kann auch benutzerdefinierte Protokollmeldungen generieren, die an alle registrierten Logger weitergeleitet werden. Jeder Logger kann die Nachrichten filtern und entsprechende Maßnahmen ergreifen.

Es gibt zwei Implementierungen für `PTLogFactory`:

* Zum Überwachen von Protokollen.
* Zum Hinzufügen von Protokollen zu einer `PTLogFactory`.

## Protokolle abrufen {#listen-to-logs}

So registrieren Sie sich für das Listening von Protokollen:
1. Implementieren einer benutzerdefinierten Klasse, die dem Protokoll folgt `PTLogger`:

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

1. Um die Instanz für den Empfang von Protokolleinträgen zu registrieren, fügen Sie eine Instanz der `PTLogger` der `PTLoggerFactory`:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

Im Folgenden finden Sie ein Beispiel für das Filtern von Protokollen mithilfe der `PTLogEntry` Typ:

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

## Neue Protokollmeldungen hinzufügen {#add-new-log-messages}

So registrieren Sie sich, um Protokolle zu überwachen:

Erstellen Sie eine neue `PTLogEntry` und fügen Sie ihn zu `thePTLogFactory`:

Sie können eine `PTLogEntry` und fügen Sie sie zum `PTLogFactory` freigegebene Instanz oder verwenden Sie eines der Makros, um dieselbe Aufgabe durchzuführen.

Im Folgenden finden Sie ein Beispiel für die Protokollierung mit der `PTLogDebug` macro:

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
