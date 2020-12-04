---
description: 'null'
seo-description: 'null'
seo-title: Sicheres Laden von Anzeigen über HTTPS
title: Sicheres Laden von Anzeigen über HTTPS
uuid: 18be77cc-c59b-4982-b8c1-e4451495edd2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Sicheres Laden von Anzeigen über HTTPS {#secure-ad-loading-over-https}

Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigen-Server und CRS-bezogene Aufrufe über HTTPS.

Die Funktion ist nicht standardmäßig aktiviert. Verwenden Sie Folgendes, um sicheres Laden der Anzeige zu aktivieren.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
