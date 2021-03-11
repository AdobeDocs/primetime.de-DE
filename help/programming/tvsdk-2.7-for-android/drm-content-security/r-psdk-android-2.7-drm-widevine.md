---
description: Sie können das native Widevine DRM von Android mit DASH-Streams verwenden.
title: Widevine DRM
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---


# Widevine DRM {#widevine-drm}

Sie können das native Widevine DRM von Android mit DASH-Streams verwenden.

Rufen Sie die folgende `com.adobe.mediacore.drm.DRMManager`-API auf, bevor Sie die Wiedergabe starten:

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

Argumente:

* `drm` -  `"com.widevine.alpha"` für Widevine.

* `licenseServerURL` - Die URL des Widevine-Lizenzservers, der Lizenzanforderungen erhält.
* `requestProperties` - Enthält zusätzliche Header, die in die ausgehende Lizenzanforderung aufgenommen werden sollen.

Verwenden Sie beispielsweise bei der Verwendung von für Expressplay DRM verpackten Inhalten den folgenden Code vor der Wiedergabe:

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```

