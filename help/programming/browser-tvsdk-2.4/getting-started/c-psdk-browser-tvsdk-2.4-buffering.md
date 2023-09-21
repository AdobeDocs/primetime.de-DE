---
description: Sie können Visualisierungen konfigurieren, um den Benutzer darüber zu informieren, dass Inhalte gepuffert werden.
title: Pufferung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---

# Pufferung{#buffering}

Sie können Visualisierungen konfigurieren, um den Benutzer darüber zu informieren, dass Inhalte gepuffert werden.

Suchen Sie nach `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` und `AdobePSDK.PSDKEventType.BUFFERING_END` -Ereignisse. Beispiel:

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

Das UI Framework bietet eine standardmäßige Implementierung des Pufferüberlagerungsverhaltens, die wie unten gezeigt erweitert werden kann:

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

So sieht das Ergebnis-DOM aus:

```
<div id=" videoDiv" class="ptp-root-element"> 
<div name="videoPlayer" value="videoPlayer" class="ptp-main-video-div-style"> 
<div name="bufferingOverlay" value="bufferingOverlay" class="ptp-buffering-overlay my_buffering_overlay_bar'"></div> 
</div> 
</div> 
```
