---
description: 'null'
seo-description: 'null'
seo-title: Pre-Roll-Anzeigen deaktivieren
title: Pre-Roll-Anzeigen deaktivieren
uuid: 2e307a58-49f2-43d6-908b-97684ad6e3d3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 0%

---


# Pre-Roll-Anzeigen deaktivieren{#disable-pre-roll-ads}

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

