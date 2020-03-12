---
description: Code kann einen Schlüssel über DRMManager anfordern.
seo-description: Code kann einen Schlüssel über DRMManager anfordern.
seo-title: Arbeitsablauf für Schlüsselanforderungen in HTML5 TVSDK
title: Arbeitsablauf für Schlüsselanforderungen in HTML5 TVSDK
uuid: a1f50eba-4301-49a1-b2e5-9add6687cff8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Arbeitsablauf für Schlüsselanforderungen in HTML5 TVSDK{#key-request-workflow-on-html-tvsdk}

Code kann einen Schlüssel über DRMManager anfordern.

Das Browser TVSDK stellt außerdem eine setProtectionData-API über das DRMManager-Objekt bereit:

```
[  /** 
   * This will only work for MSE. 
   * <p> Attach key system specific data to use for DRM 
license acquisition. </p> 
   * @param {Object} protectionData - an object containing property names corresponding to key system name strings 
   * (e.g. "org.w3.clearkey") and associated values being instances of 
   * MediaPlayer.vo.protection.ProtectionData. 
   * @returns {AdobePSDK.PSDKErrorCode} kECSuccess or one of the error codes. 
   * @function 
   * @memberof AdobePSDK.DRMManager# 
   */ 
   setProtectionData: function(protectionData) 
```

Ihr Code muss diese API aufrufen, bevor die Inhaltswiedergabe normal gestartet wird. MediaPlayer.vo.protection.ProtectionData ist hier dokumentiert: [https://vm2.dashif.org/dash.js/docs/jsdocs/MediaPlayer.vo.protection.ProtectionData.html](https://vm2.dashif.org/dash.js/docs/jsdocs/MediaPlayer.vo.protection.ProtectionData.html)

Im Folgenden finden Sie ein Beispiel für ein Datenschutzdatenobjekt mit Lizenz-Server-URLs für PlayReady und Widevine.

```
var protectionData = { 
   "com.widevine.alpha": { 
                          "serverURL": "https://wv.service.expressplay.com/hms/wv/rights/ 
                           ?ExpressPlayToken=AQAAABIDKA4AAABQuPPoebWWZZD2l3APRKkkagEDOXm 
                           CjgbhsqJTYeZ9KabkjCvSLvuXGHiVLymBnouGXDdCKpbz5IvB3jCZp9U05pys 
                           l9eavucsWXnA0tafbM-1SSJKXOa70kvxAJ_ybhdcmy7-6g" 
                          }, 
   "com.microsoft.playready": { 
                               "serverURL": "https://expressplay-licensing.axprod.net/ 
                                LicensingService.ashx?ExpressPlayToken=AQAAAw_ZXqcAAAB 
                                gHD1gnn_AMQJKfFCP3k9zbBw2srzBLryJVLXclnjhcSBCz4TBzrtfe 
                                gmSw1hAKdFHTNL-KVBGsI4ygBnfPRBUCvGsVOwpQ944fhq45W06ygJ 
                                roB2xOrM03tbkWcrthI7y_UQdHzufHjcBqKZm8QDoqKpxrxc" 
                               } 
   };
```

TVSDK stellt keine API bereit, um ein bestimmtes DRM-System zu erzwingen, da jeder Browser nur ein DRM-System unterstützt.
