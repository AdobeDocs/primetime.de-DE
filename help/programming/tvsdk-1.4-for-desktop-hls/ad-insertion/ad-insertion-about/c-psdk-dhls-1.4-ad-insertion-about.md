---
description: Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.
title: Anzeigen einfügen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# Übersicht {#inserting-ads-overview}

Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.

Ein *`ad break`* enthält eine oder mehrere Anzeigen, die nacheinander abgespielt werden. TVSDK fügt Anzeigen in den Hauptinhalt als Mitglieder einer oder mehrerer Werbeunterbrechungen ein.

## Pre-Roll-Anzeigen {#disable-preroll-ads} deaktivieren

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
