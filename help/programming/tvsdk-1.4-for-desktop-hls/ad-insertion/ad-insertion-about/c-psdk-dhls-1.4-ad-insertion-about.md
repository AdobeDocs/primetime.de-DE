---
description: Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.
seo-description: Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.
seo-title: Anzeigen einfügen
title: Anzeigen einfügen
uuid: 25c79822-a861-427b-b6a8-24714b21aae4
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Übersicht {#inserting-ads-overview}

Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.

Eine *`ad break`* enthält eine oder mehrere Anzeigen, die nacheinander abgespielt werden. TVSDK fügt Anzeigen in den Hauptinhalt als Mitglieder einer oder mehrerer Werbeunterbrechungen ein.

## Pre-Roll-Anzeigen deaktivieren {#disable-preroll-ads}

Um Pre-Roll zu deaktivieren, ändern Sie die standardmäßigen Opportunitätserzeuger, um den Pre-Roll-Aufruf nicht vorzunehmen. Die standardmäßigen Opportunitätsgeneratoren sind:

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
result.push(new AdSignalingModeOpportunityGenerator()); 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```

Um die Pre-Roll-Funktion für Live-Streams zu deaktivieren, ändern Sie die obige Option, sodass nur SpliceOutOpportunityGenerator enthalten ist:

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
if (preroll_enabled == true) { result.push(new AdSignalingModeOpportunityGenerator()); } 
 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```
