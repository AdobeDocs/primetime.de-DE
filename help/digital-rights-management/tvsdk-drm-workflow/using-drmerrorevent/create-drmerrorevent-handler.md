---
seo-title: DRMErrorEvent-Handler erstellen
title: DRMErrorEvent-Handler erstellen
uuid: dde660fc-6899-47d4-97d4-46acda2db262
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc
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

