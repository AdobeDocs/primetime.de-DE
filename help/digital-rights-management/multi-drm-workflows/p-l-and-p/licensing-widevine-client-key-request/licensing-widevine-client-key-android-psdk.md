---
description: Client-Code gibt Daten an eine Android-API weiter.
seo-description: Client-Code gibt Daten an eine Android-API weiter.
seo-title: Arbeitsablauf für Schlüsselanforderungen auf Android PSDK
title: Arbeitsablauf für Schlüsselanforderungen auf Android PSDK
uuid: 575163de-0f96-434d-a3ff-7e114caf72de
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Arbeitsablauf für Schlüsselanforderungen auf Android-PSDK{#key-request-workflow-on-android-psdk}

Client-Code gibt Daten an eine Android-API weiter.

Unter Android sollte Ihr Clientcode die Lizenzserver-URL und die zugehörigen Lizenzakquise-Daten mit der folgenden API übermitteln:

```
class DRMManager 
   { 
   ... 
   /* 
   * Set the license server URL and attached request properties that the PSDK should use for the passed in drm type.  
   * 
   * drmType: "com.widevine.alpha" for widevine. "com.microsoft.playready" for playready. 
   * licenseServerURL: self explanatory.  
   * requestProperties: key value pairs to be attached as HTTP headers to all license request sent to the passed in license server URL. Pass in 
   * NULL if none is needed.  
   */ 
   public static void setProtectionData(String drmType, String licenseServerURL,  Map<String, String> requestProperties); 
    }
```

Nach dem erfolgreichen Aufruf dieser API kann Ihr Code dann die Wiedergabe von Beginn wie gewohnt durchführen. Wenn Sie Expressplay verwenden, können Sie das Token entweder als Teil der Lizenzserver-URL oder als Anforderungseigenschaft übergeben und das Token aus der Lizenzserver-URL entfernen.

Einige Android-Geräte unterstützen sowohl Widevine als auch PlayReady. Auf solchen Geräten sollte der Kunde PSDK zwingen, den Inhalt mit einem bestimmten DRM zu entschlüsseln, wenn der Inhalt mehrere DRM-Header hat. Dies kann durch Aufruf der folgenden API vor der Wiedergabe erfolgen:

```
class MediaPlayer 
   { 
   ... 
    
   /* 
   * drm: pass in "com.widevine.alpha" for widevine or "com.microsoft.playready" for playready 
   * 
   */ 
   public void setDRMScheme(String drm) throws MediaPlayerException 
   }
```

