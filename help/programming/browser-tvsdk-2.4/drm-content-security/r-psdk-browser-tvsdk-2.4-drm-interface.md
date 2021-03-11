---
description: Browser TVSDK bietet eine DRM-Schnittstelle, mit der Sie Inhalte abspielen können, die durch verschiedene DRM-Lösungen geschützt sind, einschließlich FairPlay, PlayReady und Widevine.
title: Übersicht über die DRM-Oberfläche
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Übersicht über die DRM-Oberfläche{#drm-interface-overview}

Browser TVSDK bietet eine DRM-Schnittstelle, mit der Sie Inhalte abspielen können, die durch verschiedene DRM-Lösungen geschützt sind, einschließlich FairPlay, PlayReady und Widevine.

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>DRM-Unterstützung ist für MPEG-Dash-Streams verfügbar, die mit Microsoft PlayReady (im Internet Explorer unter Windows 8.1 und Edge) und Widevine (unter Google Chrome) DRM-Systemen geschützt sind. DRM-Unterstützung ist für HLS-Streams in Safari verfügbar, die mit FairPlay geschützt sind.

Die wichtigste Schnittstelle des DRM-Workflows ist das `DRMManager`. Ein Verweis auf die `DRMManager`-Instanz kann über die MediaPlayer-Instanz abgerufen werden:

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

Im Folgenden finden Sie einen Workflow auf hoher Ebene für die Wiedergabe von DRM-geschützten Inhalten:

1. Um die DRM-systemspezifischen Daten anzuhängen, die von Browser TVSDK beim Lizenzerwerb für einen geschützten Stream verwendet werden, führen Sie den folgenden Aufruf aus, bevor Sie `mediaPlayer.replaceCurrentResource` aufrufen:

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
          "serverURL": { 
             "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
             "license-request": "https://example.com:8096/flashaccess/req", 
             "license-release": "https://example.com:8096/flashaccess/req" 
          }, 
          "httpRequestHeaders": { 
          } 
       } 
   }; 
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. Wenn derselbe Inhalt in verschiedenen Browsern mit unterschiedlichen DRM-Systemen verwendet werden soll, können Schutzdaten für mehrere DRM-Systeme angegeben werden.

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
           "serverURL": { 
               "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
               "license-request": "https://example.com:8096/flashaccess/req", 
               "license-release": "https://example.com:8096/flashaccess/req" 
           }, 
           "httpRequestHeaders": { 
           } 
       }, 
       "com.widevine.alpha": { 
           "serverURL": "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "dt-custom-data": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.microsoft.playready": { 
           "serverURL": "https://pr.test.expressplay.com/playready/RightsManager.asmx?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "http-header-CustomData": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.apple.fps.1_0": { 
           "serverURL": "https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<token value>", 
           "certificateURL": "Path_To_certificate.cer", 
           "licenseResponseType": "arraybuffer", 
           "httpRequestHeaders": { 
               "Content-type": "application/octet-stream" 
           } 
       }, 
       "org.w3.clearkey": { 
           "clearkeys": { 
               "H3JbV93QV3mPNBKQON2UtQ": "ClKhDPHMtCouEx1vLGsJsA", 
               "IAAAACAAIAAgACAAAAAAAg": "5t1CjnbMFURBou087OSj2w" 
           } 
       } 
   }; 
   
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. Wenn keine Schutzdaten festgelegt sind, werden nötige Informationen wie die Lizenz-URL gegebenenfalls aus dem Feld PSSH für DRM-Systeme abgerufen.

   >[!TIP]
   >
   >Durch Angabe von Schutzdaten wird die im Feld &quot;PSSH&quot;angegebene Lizenz-URL außer Kraft gesetzt.

1. Standardmäßig ist der Sitzungstyp für die DRM-Lizenz temporär, d. h. die Lizenz wird nach dem Schließen der Sitzung nicht gespeichert.

   Sie können einen Sitzungstyp mit einer API in `DRMManager` angeben.  Zur Abwärtskompatibilität gehören die Sitzungstypen `temporary`, `persistent-license`, `persistent-usage-record` und `persistent`.

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. Wenn `sessionType` oder `persistent-license` oder `persistent` verwendet wird, kann die DRM-Lizenz zurückgegeben werden, indem `DRMManager.returnLicense` aufgerufen wird.

   ```js
   var onLicenseReturnFunc = function () { 
       console.log("DRM: License Return Complete "); 
   }, 
   
   onLicenseReturnErrorFunc = function (major, minor, errorString/*, errorServerUrl*/) { 
      console.log("DRM: License Return Error: " + errorString); 
   }, 
   
   drmManager = mediaPlayer.drmManager; 
   
   if (drmManager) { 
       var returnLicenseListener = new  
           AdobePSDK.DRMReturnLicenseListener(onLicenseReturnFunc, onLicenseReturnErrorFunc); 
       drmManager.returnLicense(null, null, null, false, returnLicenseListener, drmLicense.session); 
   }
   ```

