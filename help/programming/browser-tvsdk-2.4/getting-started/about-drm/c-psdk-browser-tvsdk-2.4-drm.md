---
description: Sie können DRM-spezifische Workflows (Digital Rights Management) ausführen.
title: Digital Rights Management
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Digital Rights Management {#digital-rights-management}

Sie können DRM-spezifische Workflows (Digital Rights Management) ausführen.

Sie können die `AdobePSDK.DRMMetadataInfoEvent` -Ereignis zur Verarbeitung von DRM-Workflows:

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## Digital Rights Management hinzufügen {#add-digital-rights-management}

1. Fügen Sie die `DRMMetadataInfoAvailableEvent` um die `DRMMetadata`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. Implementieren des `onDRMMetadataInfoAvailable` -Abschnitt über der Zeile in Schritt 1.

   ```js
   var onDRMMetadataInfoAvaialble = function(event) { 
    var drmMetadataInfo = event.drmMetadataInfo; 
    var drmMetadata = null; 
   
    if(drmMetadataInfo) { 
     drmMetadata = drmMetadataInfo.drmMetadata; 
    } 
   
    drmManager.acquireLicense(drmMetadata, null, null); 
   };
   ```

1. Erstellen Sie den DRMManager in der Methode setupVideo .

   ```js
   var drmManager = player.drmManager;
   ```

1. Erstellen Sie die Schutzdaten für Widevine und PlayReady, indem Sie das folgende Beispiel kopieren:

   ```js
   var protectionData = { 
     "com.widevine.alpha":{ 
       "serverURL":"https://wv.service.expressplay.com/hms/wv/rights/? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]"  
     }, 
   
     "com.microsoft.playready":{ 
       "serverURL":"https://pr.test.expressplay.com/playready/RightsManager.asmx? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]", 
         "httpRequestHeaders":{ 
       } 
     } 
   };
   ```

1. Fügen Sie die Schutzdaten zum drmManager hinzu.

   ```js
   drmManager.setProtectionData(protectionData);
   ```

1. Ändern Sie die Ressourcen-URL in einen DASH-Test-Stream.

   >[!TIP]
   >
   >Stellen Sie sicher, dass Sie den Ressourcentyp aktualisieren, da es sich jetzt um DASH handelt.

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. Testen Sie Ihre Konfiguration.
