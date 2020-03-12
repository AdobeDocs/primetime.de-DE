---
seo-title: DRMStatusEvent-Handler erstellen
title: DRMStatusEvent-Handler erstellen
uuid: 64f539d9-344c-4372-88b8-c8d098af9dd8
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# DRMStatusEvent-Handler erstellen{#create-a-drmstatusevent-handler}

Im folgenden Beispiel wird ein Ereignis-Handler erstellt, der die DRM-Inhaltsstatusinformationen für das Primetime-Objekt ausgibt, von dem das Ereignis stammt.

Hinzufügen Sie einen Ereignis-Handler zu einem Primetime-Objekt, das auf geschützten Inhalt verweist:

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

