---
description: Client-Code übergibt Daten an eine Android-API.
title: Workflow für Schlüsselanforderungen in Android PSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Workflow für Schlüsselanforderungen in Android PSDK{#key-request-workflow-on-android-psdk}

Client-Code übergibt Daten an eine Android-API.

Unter Android sollte Ihr Clientcode die Lizenzserver-URL und die zugehörigen Lizenzakquise-Daten mithilfe der folgenden API übergeben:

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

Nachdem Sie diese API erfolgreich aufgerufen haben, kann Ihr Code die Inhaltswiedergabe auf die übliche Weise starten. Wenn Sie &quot;Expressplay&quot;verwenden, können Sie das Token entweder als Teil der Lizenzserver-URL oder als Anfrageeigenschaft übergeben und das Token aus der Lizenzserver-URL entfernen.

Einige Android-Geräte unterstützen sowohl Widevine als auch PlayReady. Auf solchen Geräten kann der Kunde PSDK zwingen, den Inhalt mit einem bestimmten DRM zu entschlüsseln, wenn der Inhalt mehrere DRM-Header enthält. Dies kann durch Aufruf der folgenden API vor der Wiedergabe erfolgen:

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
