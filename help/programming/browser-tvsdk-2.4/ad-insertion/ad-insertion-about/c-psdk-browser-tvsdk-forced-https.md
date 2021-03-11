---
title: Sicheres Laden der Anzeige über HTTPS
description: Sicheres Laden der Anzeige über HTTPS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# Secure Ad Loading over HTTPS{#secure-ad-loading-over-https}

Adobe Primetime kann Anzeigen-Server von Drittanbietern über HTTPS anfordern, auch wenn der Player auf HTTP gehostet wird. Nur diese Ad-Server-Aufrufe werden auf HTTPS aktualisiert, die der Client während der Auditude Ad-Resolver-Phase durchsucht.

>[!NOTE]
>
>Diese Funktion wird für Flash nicht unterstützt.

Verwenden Sie Folgendes, um sicheres Laden der Anzeige zu aktivieren. Es ist nicht standardmäßig aktiviert.

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
