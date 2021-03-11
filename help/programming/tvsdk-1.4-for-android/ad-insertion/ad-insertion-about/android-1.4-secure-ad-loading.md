---
title: Sicheres Laden von Anzeigen über HTTPS
description: Sicheres Laden von Anzeigen über HTTPS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---


# Sicheres Laden von Anzeigen über HTTPS{#secure-ad-loading-over-https}

Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigen-Server und CRS-bezogene Aufrufe über HTTPS.

Die Funktion ist nicht standardmäßig aktiviert. Verwenden Sie Folgendes, um sicheres Laden der Anzeige zu aktivieren.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

