---
description: 'null'
seo-description: 'null'
seo-title: Sicheres Laden der Anzeige über HTTPS
title: Sicheres Laden der Anzeige über HTTPS
uuid: 10657f59-cfbf-4c75-9249-fc154952bc51
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '73'
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
