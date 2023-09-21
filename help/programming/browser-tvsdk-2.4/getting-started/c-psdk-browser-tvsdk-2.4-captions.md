---
description: Sie können beim Abspielen von Videoinhalten Beschriftungen anzeigen.
title: Untertitel
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# Untertitel{#captions}

Sie können beim Abspielen von Videoinhalten Beschriftungen anzeigen.

Zur Handhabung von Beschriftungen müssen Sie die `AdobePSDK.PSDKEventType.CAPTIONS_UPDATED` Ereignis-Listener:

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

Das UI Framework bietet eine standardmäßige Implementierung des Verhaltens von Untertiteln, die geändert werden kann. Das Verhalten von verdeckten Untertiteln kann auch geändert werden, indem das standardmäßige Verhalten von verdeckten Untertiteln erweitert wird. Beispiel:

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
