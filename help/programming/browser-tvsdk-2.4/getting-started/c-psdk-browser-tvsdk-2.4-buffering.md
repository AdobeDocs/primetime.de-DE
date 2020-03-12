---
description: Sie können Visualisierungen konfigurieren, um den Benutzer darüber zu informieren, dass Inhalte gepuffert werden.
seo-description: Sie können Visualisierungen konfigurieren, um den Benutzer darüber zu informieren, dass Inhalte gepuffert werden.
seo-title: Pufferung
title: Pufferung
uuid: da9498ee-c736-4093-97a2-250d3ad56d49
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Pufferung{#buffering}

Sie können Visualisierungen konfigurieren, um den Benutzer darüber zu informieren, dass Inhalte gepuffert werden.

Hör auf `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` und `AdobePSDK.PSDKEventType.BUFFERING_END` Ereignisse. Beispiel:

```js
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_BEGIN,  
                        function (event) { 
                            buffering = true; 
                            // add buffering layer 
                        }); 
  
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_END,  
                        function (event) { 
                           buffering = false; 
                           // remove buffering layer 
                        });
```

Das UI-Framework bietet eine standardmäßige Implementierung des Pufferüberlagerungsverhaltens, die wie folgt erweitert werden kann:

```js
// Using UI Framework 
function myBufferingOverlayBehavior (element, configuration, player, localize, baseLog) { 
    return ptp.bufferingOverlayBehavior(element, configuration, player, localize, baseLog); 
} 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource:'Specify Resource URL', 
        bufferingOverlay: { 
            behavior: myBufferingOverlayBehavior, 
            classNames: 'ptp-buffering-overlay my_buffering_overlay_bar' 
        } 
    } 
 
}); 
```

So sieht das Ergebnis von DOM aus:

```
<div id=" videoDiv" class="ptp-root-element"> 
<div name="videoPlayer" value="videoPlayer" class="ptp-main-video-div-style"> 
<div name="bufferingOverlay" value="bufferingOverlay" class="ptp-buffering-overlay my_buffering_overlay_bar'"></div> 
</div> 
</div> 
```

