---
description: Sie können Visualisierungen konfigurieren, um den Benutzer darüber zu informieren, dass Inhalte gepuffert werden.
title: Pufferung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 3%

---


# Pufferung{#buffering}

Sie können Visualisierungen konfigurieren, um den Benutzer darüber zu informieren, dass Inhalte gepuffert werden.

Suchen Sie nach den Ereignissen `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` und `AdobePSDK.PSDKEventType.BUFFERING_END`. Beispiel:

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

