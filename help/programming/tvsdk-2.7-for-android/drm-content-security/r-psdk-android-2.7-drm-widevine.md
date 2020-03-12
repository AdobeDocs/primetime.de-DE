---
description: Sie können das native Widevine DRM von Android mit DASH-Streams verwenden.
seo-description: Sie können das native Widevine DRM von Android mit DASH-Streams verwenden.
seo-title: Widevine DRM
title: Widevine DRM
uuid: ceb2f18f-9e53-47d6-9d4b-7004ac1d22c9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Widevine DRM {#widevine-drm}

Sie können das native Widevine DRM von Android mit DASH-Streams verwenden.

Rufen Sie die folgende `com.adobe.mediacore.drm.DRMManager` API auf, bevor Sie die Wiedergabe starten:

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

Argumente:

* `drm` - `"com.widevine.alpha"` für Widevine.

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

