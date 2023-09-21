---
title: Werbung hinzufügen
description: Werbung hinzufügen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Werbung hinzufügen {#add-advertising}

1. Definieren Sie die Werbe-Metadaten.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. Fügen Sie die Anzeigen-Metadaten zum `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. Fügen Sie die Einstellungen zur Konfiguration hinzu und fügen Sie eine `SpliceOut` Parserfabrik.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. Fügen Sie die `ExtCueOutContentFactory` in den Bibliotheksabschnitt.
1. Laden Sie die `ExtCueOutContentFactory.js` aus dem Bibliotheksabschnitt aus und legen Sie ihn im Arbeitsordner ab.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Testen Sie Ihre Konfiguration.
