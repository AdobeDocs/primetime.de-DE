---
description: Sie können das native Widevine DRM von Android mit DASH-Streams verwenden.
title: Widevine DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

Sie können das native Widevine DRM von Android mit DASH-Streams verwenden.

Rufen Sie Folgendes auf `com.adobe.mediacore.drm.DRMManager` API vor Beginn der Wiedergabe:

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

Argumente:

* `drm` - `"com.widevine.alpha"` für Widevine.

* `licenseServerURL` - Die URL des Widevine-Lizenzservers, der Lizenzanfragen erhält.
* `requestProperties` - Enthält zusätzliche Header, die in die ausgehende Lizenzanfrage aufgenommen werden sollen.

Wenn Sie beispielsweise Inhalte verwenden, die für Expression DRM verpackt sind, verwenden Sie vor der Wiedergabe den folgenden Code:

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```
