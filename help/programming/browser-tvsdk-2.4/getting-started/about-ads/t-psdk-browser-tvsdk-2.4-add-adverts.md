---
description: 'null'
seo-description: 'null'
seo-title: Hinzufügen
title: Hinzufügen
uuid: 7762506f-b55e-445d-b8a2-c1208358a370
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Hinzufügen {#add-advertising}

1. Definieren Sie die Anzeigenmetadaten.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. Hinzufügen Sie die Anzeigenmetadaten an die `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. Hinzufügen Sie die Einstellungen der Konfiguration und fügen Sie eine `SpliceOut` Parser-Factory hinzu.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. Hinzufügen Sie den Abschnitt `ExtCueOutContentFactory` zur Bibliothek an.
1. Laden Sie die Datei `ExtCueOutContentFactory.js` aus dem Bibliotheksbereich herunter und legen Sie sie im Arbeitsordner ab.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Testen Sie Ihre Konfiguration.
