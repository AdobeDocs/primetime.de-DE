---
description: Sie können die Position und Größe der Videoansicht mithilfe des MediaPlayerView -Objekts steuern.
title: Position und Größe der Videoansicht steuern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Position und Größe der Videoansicht steuern{#control-the-position-and-size-of-the-video-view}

Sie können die Position und Größe der Videoansicht mithilfe des MediaPlayerView -Objekts steuern.

Browser TVSDK versucht standardmäßig, das Seitenverhältnis der Videoansicht beizubehalten, sobald sich die Größe oder Position des Videos aufgrund einer Änderung durch die Anwendung, eines Profilwechsels, eines Inhaltswechsels usw. ändert.

Sie können das standardmäßige Seitenverhältnisverhalten außer Kraft setzen, indem Sie eine andere *Skalierungspolitik*. Geben Sie die Skalierungsrichtlinie mithilfe der `MediaPlayerView` -Objekt `scalePolicy` -Eigenschaft. Die standardmäßige Skalierungsrichtlinie von `MediaPlayerView` mit einer Instanz der `MaintainAspectRatioScalePolicy` -Klasse. Um die Skalierungsrichtlinie zurückzusetzen, ersetzen Sie die Standardinstanz von `MaintainAspectRatioScalePolicy` on `MediaPlayerView.scalePolicy` mit Ihrer eigenen Richtlinie.

>[!IMPORTANT]
>
>Sie können die `scalePolicy` -Eigenschaft auf einen Nullwert.

## Fallback-Szenarien ohne Flash {#non-flash-fallback-scenarios}

In Nicht-Flash-Fallback-Szenarios funktioniert das Videodiv-Element, das im `View` -Konstruktor sollte Werte ungleich null für `offsetWidth` und `offsetHeight`. Um ein Beispiel für eine fehlerhafte Funktion anzugeben, wird die Variable `View` -Konstruktor gibt null für zurück `offsetWidth` oder `offsetHeight`.

>[!NOTE]
>
>Die CustomScalePolicy unterstützt einige wenige Browser, insbesondere IE, Edge und Safari 9, nur eingeschränkt. Bei diesen Browsern kann das native Seitenverhältnis des Videos nicht geändert werden. Die Position und Abmessungen des Videos werden jedoch gemäß der Skalierungsrichtlinie erzwungen.

1. Implementieren des `MediaPlayerViewScalePolicy` -Schnittstelle, um eine eigene Skalierungsrichtlinie zu erstellen.

   Die `MediaPlayerViewScalePolicy` verfügt über eine Methode:

   ```js
   /** 
   * Adjust the specified rectangle to match the new video dimensions. 
   * @param viewPort {AdobePSDK.Rectangle}The video rectangle as absolute position. 
   * @param videoWidth {Number}The video width. 
   * @param videoHeight {Number} The video height. 
   * @return {AdobePSDK.Rectangle} an adjusted rectangle. 
   */ 
   function adjustCallbackFunc(viewPort, videoWidth, videoHeight);
   ```

   Beispiel:

   ```js
   /** 
   Default Constructor 
   */ 
   MediaPlayerViewCustomScalePolicy = function() { 
       return this; 
   }; 
   MediaPlayerViewCustomScalePolicy.prototype = { 
       constructor: MediaPlayerViewScalePolicy, 
       adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
           /* Your Custom Adjustment here. */ 
           [...] 
           return adjustedRectangle; 
       } 
   };
   ```

1. Weisen Sie Ihre Implementierung dem `MediaPlayerView` -Eigenschaft.

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. Hinzufügen Ihrer Ansicht zum Medienplayer `view` -Eigenschaft.

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**Beispiel: Skalieren Sie das Video, um die gesamte Videoansicht auszufüllen, ohne das Seitenverhältnis beizubehalten:**

```
/** 
 * Default constructor. 
 */ 
MediaPlayerViewCustomScalePolicy = function() { 
    return this; 
}; 
MediaPlayerViewCustomScalePolicy.prototype = { 
    constructor: MediaPlayerViewScalePolicy, 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
        return viewPort; 
    } 
}; 
var view = new AdobePSDK.MediaPlayerView(videoDiv); 
view.scalePolicy = new MediaPlayerViewCustomScalePolicy (); 
mediaPlayer.view = view;
```
