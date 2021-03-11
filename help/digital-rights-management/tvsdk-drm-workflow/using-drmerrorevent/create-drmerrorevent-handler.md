---
title: DRMErrorEvent-Handler erstellen
description: DRMErrorEvent-Handler erstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# DRMErrorEvent-Handler erstellen{#create-a-drmerrorevent-handler}

Erstellen Sie einen Ereignis-Handler, um von Primetime ausgelöste Fehlermeldungen zu verarbeiten, wenn beim Abspielen geschützter Ereignisse ein Fehler auftritt.

Wenn eine Anwendung auf einen Fehler stößt, führt sie normalerweise eine beliebige Anzahl von Aufgaben durch. Er informiert den Benutzer dann über den Fehler und stellt Optionen zur Lösung des Problems bereit.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```

