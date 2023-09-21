---
title: Sicheres Laden von Anzeigen über HTTPS
description: Sicheres Laden von Anzeigen über HTTPS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# Sicheres Laden von Anzeigen über HTTPS{#secure-ad-loading-over-https}

Adobe Primetime kann Werbeserver von Drittanbietern über HTTPS anfordern, selbst wenn der Player auf HTTP gehostet wird. Nur diese Ad-Server-Aufrufe werden auf HTTPS aktualisiert, das der Client während der Auditude Ad Resolver-Phase durchsucht.

>[!NOTE]
>
>Diese Funktion wird für Flash nicht unterstützt.

Verwenden Sie Folgendes, um sicheres Laden von Anzeigen zu aktivieren. Sie ist standardmäßig nicht aktiviert.

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
