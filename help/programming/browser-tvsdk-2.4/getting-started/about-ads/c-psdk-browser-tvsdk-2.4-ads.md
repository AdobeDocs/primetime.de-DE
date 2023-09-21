---
description: Wenn Inhalt wiedergegeben wird, kann Browser TVSDK Anzeigen anzeigen und Informationen über Anzeigen weitergeben, wenn das MediaResource -Objekt erstellt wird.
title: Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Übersicht {#ads-overview}

Wenn Inhalt wiedergegeben wird, kann Browser TVSDK Anzeigen anzeigen und Informationen über Anzeigen weitergeben, wenn das MediaResource -Objekt erstellt wird.

Sie können optional die `prepareToPlay` Funktion nach dem Empfang `AdobePSDK.MediaPlayerStatus.INITIALIZED`.

```js
function onStatusChange (event) { 
   switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
        player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
        break; 
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
        player.play(); 
        break; 
   } 
} 
 
var auditudeSettings     = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.domain  = "sample_auditude_domain"; 
auditudeSettings.mediaId = "sample_media_id"; 
auditudeSettings.zoneId  = "sample_zone_id"; 
 
// event handler 
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
 
var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
```

Browser TVSDK bietet außerdem die folgenden anzeigenspezifischen Ereignisse, die Sie in Ihren Ereignishandlern verwenden können, um zu verhindern, dass Inhalte bei der Wiedergabe von Anzeigen schnell weitergeleitet werden:

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`
* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

Um dies im UI Framework zu sehen, geben Sie die Anzeigeneinstellungen in der Konfiguration wie folgt an:

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource: { 
 
            resourceUrl:'Specify Resource Url', 
 
            auditudeSettings: { 
                validMimeTypes: ["application/x-mpeURL"], 
                domain: "Sample_auditude_domain", 
                mediaId:"sample_media_id", 
                zoneID:"sample_zone_id", 
                creativeRepackagingEnabled:true 
            } 
        } 
    } 
}; 
```

Weitere Informationen zu den erforderlichen `AuditudeSettings`, siehe [Anzeigeneinfüge-Metadaten](../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md).
