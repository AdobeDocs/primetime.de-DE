---
description: Wenn die Anwendung Ereignis verarbeiten muss, die vom Feature Manager gesendet werden, muss sie den Manager in der Datei PlayerFragment.java registrieren.
title: Umgang mit Ereignissen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 4%

---


# Umgang mit Ereignissen {#handling-events}

Wenn die Anwendung Ereignis verarbeiten muss, die vom Feature Manager gesendet werden, muss sie den Manager in der Datei PlayerFragment.java registrieren.

Beispiel:

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
