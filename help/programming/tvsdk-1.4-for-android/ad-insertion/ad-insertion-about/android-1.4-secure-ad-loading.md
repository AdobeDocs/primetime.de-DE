---
title: Laden sicherer Anzeigen über HTTPS
description: Laden sicherer Anzeigen über HTTPS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Laden sicherer Anzeigen über HTTPS{#secure-ad-loading-over-https}

Adobe Primetime bietet die Möglichkeit, den ersten Aufruf an den Primetime-Anzeigenserver und CRS-bezogene Aufrufe über HTTPS anzufordern.

Die Funktion ist standardmäßig nicht aktiviert. Verwenden Sie Folgendes, um sicheres Laden von Anzeigen zu aktivieren.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
