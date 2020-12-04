---
description: Sie können DRM-spezifische Workflows abschließen.
seo-description: Sie können DRM-spezifische Workflows abschließen.
seo-title: Digital Rights Management
title: Digital Rights Management
uuid: 011605c7-50c4-4ad5-9961-8cd92d0e6fd8
translation-type: tm+mt
source-git-commit: 5a786d8001326f874a51d65b8e8badca44f46e96
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Digital Rights Management {#digital-rights-management}

Sie können DRM-spezifische Workflows abschließen.

Sie können das `AdobePSDK.DRMMetadataInfoEvent`-Ereignis abhören, um DRM-Workflows zu bearbeiten:

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## hinzufügen Digital Rights Management {#add-digital-rights-management}

1. hinzufügen Sie `DRMMetadataInfoAvailableEvent`, um `DRMMetadata` abzurufen.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. Implementieren Sie den Abschnitt `onDRMMetadataInfoAvailable` über der Zeile in Schritt 1.

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

1. Erstellen Sie den DRMManager in der Methode setupVideo.

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

1. hinzufügen die Schutzdaten an den drmManager.

   ```js
   drmManager.setProtectionData(protectionData);
   ```

1. Ändern Sie die Ressourcen-URL in einen DASH-Teststream.

   >[!TIP]
   >
   >Stellen Sie sicher, dass Sie den Ressourcentyp aktualisieren, da es sich jetzt um DASH handelt.

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. Testen Sie Ihre Konfiguration.