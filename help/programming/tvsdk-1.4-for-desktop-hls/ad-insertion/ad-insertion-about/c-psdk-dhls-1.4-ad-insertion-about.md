---
description: Durch die Anzeigeneinfügung werden Anzeigen für Video-On-Demand (VOD) , für Live-Streaming und für lineares Streaming mit Anzeigen-Tracking und Anzeigenwiedergabe aufgelöst. TVSDK sendet die erforderlichen Anfragen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in Phasen.
title: Anzeigen einfügen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---

# Übersicht {#inserting-ads-overview}

Durch die Anzeigeneinfügung werden Anzeigen für Video-On-Demand (VOD) , für Live-Streaming und für lineares Streaming mit Anzeigen-Tracking und Anzeigenwiedergabe aufgelöst. TVSDK sendet die erforderlichen Anfragen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in Phasen.

Ein *`ad break`* enthält eine oder mehrere Anzeigen, die nacheinander abgespielt werden. TVSDK fügt Anzeigen im Hauptinhalt als Mitglieder einer oder mehrerer Werbeunterbrechungen ein.

## Pre-Roll-Anzeigen deaktivieren {#disable-preroll-ads}

Um die Pre-Roll-Funktion zu deaktivieren, ändern Sie die standardmäßigen Opportunity-Generatoren, sodass der Pre-Roll-Aufruf nicht erfolgt. Die standardmäßigen Opportunity-Generatoren sind:

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

Um die Pre-Roll-Funktion für Live-Streams zu deaktivieren, ändern Sie die obigen Parameter so, dass nur der SpliceOutOpportunityGenerator enthalten ist:

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
