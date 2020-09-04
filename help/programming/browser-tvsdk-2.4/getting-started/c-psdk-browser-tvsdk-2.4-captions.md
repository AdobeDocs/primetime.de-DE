---
description: Sie können Beschriftungen beim Abspielen von Videoinhalten anzeigen.
seo-description: Sie können Beschriftungen beim Abspielen von Videoinhalten anzeigen.
seo-title: Beschriftungen
title: Beschriftungen
uuid: 4dedcedc-50e5-4983-bb09-3f316337117e
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 3%

---


# Beschriftungen{#captions}

Sie können Beschriftungen beim Abspielen von Videoinhalten anzeigen.

Um Beschriftungen zu verarbeiten, müssen Sie den `AdobePSDK.PSDKEventType.CAPTIONS_UPDATED` Ereignis-Listener hinzufügen:

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.CAPTIONS_UPDATED,  
                        onCaptionsUpdateEvent); 
... 
function onCaptionsUpdateEvent (event) { 
  // code to show the captions icon and any settings button. 
<pre>
   For example: 
  var btnCC = document.getElementById("btn_captions"); 
   btnCC.classList.remove("invisible"); 
   
  var btnSettings = document.getElementById("btn_settings"); 
   btnSettings.classList.remove("invisible"); 
 } 
</pre>
```

Das UI-Framework bietet eine standardmäßige Verhaltensimplementierung von Beschriftungen, die geändert werden kann. Das Verhalten von Untertiteln kann auch geändert werden, indem das Verhalten von Untertiteln erweitert wird. Beispiel:

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer(‘.videoDiv', { 
player:{ 
    mediaResource: 'Specify Resource URL', 
    ccStyle: { 
    font:AdobePSDK.TextFormat.CURSIVE, 
    fontColor:AdobePSDK.TextFormat.BRIGHT_WHITE, 
    edgeColor:AdobePSDK.TextFormat.BLUE, 
    backgroundColor:AdobePSDK.TextFormat.BLACK, 
    fillColor:AdobePSDK.TextFormat.BLUE, 
    size:AdobePSDK.TextFormat.MEDIUM, 
    fontOpacity:100, 
    backgroundOpacity:1, 
    fillOpacity:1 
   } 
 } 
 
}); 
```
