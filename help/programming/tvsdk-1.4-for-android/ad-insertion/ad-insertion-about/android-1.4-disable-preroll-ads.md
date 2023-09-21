---
title: Pre-Roll-Anzeigen deaktivieren
description: Pre-Roll-Anzeigen deaktivieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 0%

---

# Pre-Roll-Anzeigen deaktivieren{#disable-pre-roll-ads}

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
