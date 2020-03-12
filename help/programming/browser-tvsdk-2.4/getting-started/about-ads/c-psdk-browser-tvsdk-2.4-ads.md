---
description: Beim Abspielen von Inhalten kann Browser TVSDK Anzeigen anzeigen und Informationen über Anzeigen weitergeben, wenn das MediaResource-Objekt erstellt wird.
seo-description: Beim Abspielen von Inhalten kann Browser TVSDK Anzeigen anzeigen und Informationen über Anzeigen weitergeben, wenn das MediaResource-Objekt erstellt wird.
seo-title: Anzeigen
title: Anzeigen
uuid: 9a5e8c83-18ce-41e8-9cb1-fdc9da903faf
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Übersicht {#ads-overview}

Beim Abspielen von Inhalten kann Browser TVSDK Anzeigen anzeigen und Informationen über Anzeigen weitergeben, wenn das MediaResource-Objekt erstellt wird.

Sie können optional die `prepareToPlay` Funktion nach dem Empfang aufrufen `AdobePSDK.MediaPlayerStatus.INITIALIZED`.

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

Browser TVSDK bietet außerdem die folgenden anzeigenspezifischen Ereignis, die Sie in Ihren Ereignis-Handlern verwenden können, um zu verhindern, dass Inhalte bei der Wiedergabe von Anzeigen schnell weitergeleitet werden:

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`
* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

Um zu sehen, wie dies im UI-Framework funktioniert, geben Sie die Anzeigeneinstellungen in der Konfiguration wie folgt an:

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

Weitere Informationen zu den erforderlichen Metadaten `AuditudeSettings`finden Sie unter [Anzeigeneinfügemetadaten](../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md).
