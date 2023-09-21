---
description: Wenn das Programm Ereignisse verarbeiten muss, die vom Feature Manager gesendet werden, muss es den Manager in der Datei PlayerFragment.java registrieren.
title: Umgang mit Ereignissen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Umgang mit Ereignissen {#handling-events}

Wenn das Programm Ereignisse verarbeiten muss, die vom Feature Manager gesendet werden, muss es den Manager in der Datei PlayerFragment.java registrieren.

Beispiel:

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
