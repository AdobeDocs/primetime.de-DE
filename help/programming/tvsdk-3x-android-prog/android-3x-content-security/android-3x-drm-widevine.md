---
description: Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu bieten. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Lösung von Adobe verwenden.
seo-description: Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu bieten. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Lösung von Adobe verwenden.
seo-title: Widevine DRM
title: Widevine DRM
uuid: 3a5fd786-4319-4e92-83b6-0f5328df6a44
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Widevine DRM {#widevine-drm}

Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu bieten. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Lösung von Adobe verwenden.

Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um aktuelle Informationen zur Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

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
