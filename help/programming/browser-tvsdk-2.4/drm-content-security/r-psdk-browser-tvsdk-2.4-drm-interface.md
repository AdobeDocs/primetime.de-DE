---
description: Browser TVSDK bietet eine DRM-Oberfläche, mit der Sie Inhalte wiedergeben können, die durch verschiedene DRM-Lösungen geschützt sind, darunter FairPlay, PlayReady und Widevine.
title: Übersicht über die DRM-Oberfläche
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Übersicht über die DRM-Oberfläche{#drm-interface-overview}

Browser TVSDK bietet eine DRM-Oberfläche, mit der Sie Inhalte wiedergeben können, die durch verschiedene DRM-Lösungen geschützt sind, darunter FairPlay, PlayReady und Widevine.

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>DRM-Unterstützung ist für MPEG-Dash-Streams verfügbar, die mit Microsoft PlayReady (im Internet Explorer unter Windows 8.1 und Edge) und Widevine (in Google Chrome) DRM-Systemen geschützt sind. DRM-Unterstützung ist für HLS-Streams in Safari verfügbar, die mit FairPlay geschützt sind.

Die wichtigste Benutzeroberfläche des DRM-Workflows ist die `DRMManager`. Ein Verweis auf die `DRMManager` -Instanz kann über die MediaPlayer-Instanz abgerufen werden:

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

Hier finden Sie einen allgemeinen Workflow für die Wiedergabe von DRM-geschützten Inhalten:

1. Um die DRM-systemspezifischen Daten anzuhängen, die vom Browser TVSDK im Lizenzakquiseprozess für einen geschützten Stream verwendet werden, rufen Sie Folgendes auf, bevor Sie aufrufen `mediaPlayer.replaceCurrentResource`:

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

1. Wenn erwartet wird, dass derselbe Inhalt in verschiedenen Browsern mit verschiedenen DRM-Systemen funktioniert, können Schutzdaten für mehrere DRM-Systeme angegeben werden.

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

1. Wenn keine Schutzdaten festgelegt sind, werden nötige Informationen wie die Lizenzierungs-URL, falls zutreffend, aus dem PSSH-Feld für DRM-Systeme abgerufen.

   >[!TIP]
   >
   >Durch die Angabe von Schutzdaten wird die im Feld &quot;PSSH&quot;angegebene Lizenz-URL überschrieben.

1. Standardmäßig ist der Sitzungstyp für die DRM-Lizenz temporär. Das bedeutet, dass die Lizenz nach dem Schließen der Sitzung nicht gespeichert wird.

   Sie können einen Sitzungstyp mithilfe einer API in `DRMManager`.  Zur Abwärtskompatibilität umfassen Sitzungstypen Folgendes: `temporary`, `persistent-license`, `persistent-usage-record`, und `persistent`.

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. Wenn die Variable `sessionType` verwendet wird `persistent-license` oder `persistent`, kann die DRM-Lizenz zurückgegeben werden, indem Sie `DRMManager.returnLicense`.

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
