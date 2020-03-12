---
description: 'null'
seo-description: 'null'
seo-title: Sicheres Laden von Anzeigen über HTTPS
title: Sicheres Laden von Anzeigen über HTTPS
uuid: 72ab94d3-ee0c-4f02-adf2-c186ae6aec26
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Sicheres Laden von Anzeigen über HTTPS {#secure-ad-loading-over-https}

Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigenserver und CRS-bezogene Aufrufe über HTTPS.

Die Funktion ist nicht standardmäßig aktiviert. Verwenden Sie Folgendes, um sicheres Laden der Anzeige zu aktivieren.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

