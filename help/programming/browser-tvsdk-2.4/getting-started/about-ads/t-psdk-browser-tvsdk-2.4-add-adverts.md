---
description: 'null'
seo-description: 'null'
seo-title: hinzufügen
title: hinzufügen
uuid: 7762506f-b55e-445d-b8a2-c1208358a370
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---


# hinzufügen Werbung {#add-advertising}

1. Definieren Sie die Anzeigenmetadaten.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. hinzufügen Sie die Anzeigenmetadaten auf `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. hinzufügen Sie die Einstellungen der Konfiguration und fügen Sie eine `SpliceOut` Parser-Factory hinzu.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. hinzufügen Sie `ExtCueOutContentFactory` in den Bibliotheksabschnitt.
1. Laden Sie das `ExtCueOutContentFactory.js` aus dem Bibliotheksabschnitt herunter und legen Sie es im Arbeitsordner ab.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Testen Sie Ihre Konfiguration.
