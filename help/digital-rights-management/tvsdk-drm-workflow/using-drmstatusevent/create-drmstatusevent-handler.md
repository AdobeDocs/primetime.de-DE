---
title: DRMStatusEvent-Handler erstellen
description: DRMStatusEvent-Handler erstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# DRMStatusEvent-Handler erstellen{#create-a-drmstatusevent-handler}

Im folgenden Beispiel wird ein Ereignis-Handler erstellt, der die DRM-Inhaltsstatusinformationen für das Primetime-Objekt ausgibt, von dem das Ereignis stammt.

hinzufügen Sie einen Ereignis-Handler zu einem Primetime-Objekt, das auf geschützten Inhalt verweist:

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

