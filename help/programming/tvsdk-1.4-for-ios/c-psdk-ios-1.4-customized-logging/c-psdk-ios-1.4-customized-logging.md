---
description: Sie können Ihr eigenes Protokollierungssystem implementieren.
seo-description: Sie können Ihr eigenes Protokollierungssystem implementieren.
seo-title: Benutzerdefinierte Protokollierung
title: Benutzerdefinierte Protokollierung
uuid: c5bdf266-4266-4896-b6e0-47710ce64e67
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Benutzerdefinierte Protokollierung {#customized-logging}

Sie können Ihr eigenes Protokollierungssystem implementieren.

Zusätzlich zur Protokollierung mithilfe vordefinierter Benachrichtigungen können Sie ein Protokollierungssystem implementieren, das Ihre Protokollmeldungen und Nachrichten verwendet, die von TVSDK generiert werden. Weitere Informationen zu vordefinierten Benachrichtigungen finden Sie unter [Das Benachrichtigungssystem](../c-psdk-ios-1.4-notification-system/c-psdk-ios-1.4-notification-system.md). Sie können diese Protokolle verwenden, um Fehler in Ihren Player-Anwendungen zu beheben und einen besseren Einblick in den Wiedergabe- und Werbeablauf zu erhalten.

Die benutzerdefinierte Protokollierung verwendet eine freigegebene Singleton-Instanz von `PSDKPTLogFactory`, die einen Mechanismus zum Protokollieren von Nachrichten an mehrere Protokollfunktionen bereitstellt. Sie definieren und fügen (registrieren) einen oder mehrere Protokollen zu `PTLogFactory` hinzu. Auf diese Weise können Sie mehrere Protokollfunktionen mit benutzerdefinierten Implementierungen definieren, z. B. eine Konsolenprotokollierung, eine Webprotokollierung oder eine Protokollfunktion für den Konsolenverlauf.

TVSDK generiert Protokollmeldungen für viele seiner Aktivitäten, die das `PTLogFactory` an alle registrierten Protokollfunktionen weiterleitet. Ihre Anwendung kann auch benutzerdefinierte Protokollmeldungen generieren, die an alle registrierten Anmelder weitergeleitet werden. Jede Protokollfunktion kann die Nachrichten filtern und entsprechende Maßnahmen ergreifen.

Es gibt zwei Implementierungen für `PTLogFactory`:

* Zum Listening von Protokollen.
* Zum Hinzufügen von Protokollen zu einem `PTLogFactory`.

## Protokolle {#listen-to-logs}

So registrieren Sie sich zum Listening von Protokollen:
1. Implementieren Sie eine benutzerdefinierte Klasse, die dem Protokoll `PTLogger` folgt:

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

1. Um die Instanz zum Empfangen von Protokolleinträgen zu registrieren, fügen Sie der `PTLoggerFactory` eine Instanz von `PTLogger` hinzu:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

Hier ein Beispiel für das Filtern von Protokollen mit dem Typ `PTLogEntry`:

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

## hinzufügen neue Protokollmeldungen {#add-new-log-messages}

So registrieren Sie sich zum Abhören von Protokollen:
1. Erstellen Sie ein neues `PTLogEntry` und fügen Sie es zu `thePTLogFactory` hinzu:

   Sie können ein `PTLogEntry` manuell instanziieren und es der freigegebenen `PTLogFactory` Instanz hinzufügen oder eines der Makros verwenden, um dieselbe Aufgabe auszuführen.

   Hier ein Beispiel für die Protokollierung mit dem Makro `PTLogDebug`:

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
