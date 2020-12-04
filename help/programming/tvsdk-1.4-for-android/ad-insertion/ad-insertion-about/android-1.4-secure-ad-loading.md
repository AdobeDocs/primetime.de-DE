---
description: 'null'
seo-description: 'null'
seo-title: Sicheres Laden von Anzeigen über HTTPS
title: Sicheres Laden von Anzeigen über HTTPS
uuid: 0d680fef-a372-4157-a89b-d9f10003c768
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Sicheres Laden von Anzeigen über HTTPS{#secure-ad-loading-over-https}

Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigen-Server und CRS-bezogene Aufrufe über HTTPS.

Die Funktion ist nicht standardmäßig aktiviert. Verwenden Sie Folgendes, um sicheres Laden der Anzeige zu aktivieren.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

