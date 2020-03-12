---
description: Wenn die Anwendung Ereignis verarbeiten muss, die vom Feature Manager gesendet werden, muss sie den Manager in der Datei PlayerFragment.java registrieren.
seo-description: Wenn die Anwendung Ereignis verarbeiten muss, die vom Feature Manager gesendet werden, muss sie den Manager in der Datei PlayerFragment.java registrieren.
seo-title: Umgang mit Ereignissen
title: Umgang mit Ereignissen
uuid: 13639f02-0dcc-4a0a-8524-515da5478006
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

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
