---
description: Mit dem MediaPlayerView-Objekt können Sie die Position und Größe der Video-Ansicht steuern.
title: Position und Größe der Video-Ansicht steuern
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Position und Größe der Video-Ansicht kontrollieren{#control-the-position-and-size-of-the-video-view}

Mit dem MediaPlayerView-Objekt können Sie die Position und Größe der Video-Ansicht steuern.

Browser TVSDK versucht standardmäßig, das Seitenverhältnis der Video-Ansicht beizubehalten, sobald sich die Größe oder Position des Videos ändert, da die Anwendung geändert wurde, ein Profil-Switch, ein Inhaltsschalter usw.

Sie können das standardmäßige Seitenverhältnis außer Kraft setzen, indem Sie eine andere *Skalierungsrichtlinie* angeben. Geben Sie die Skalierungsrichtlinie mit der Eigenschaft `MediaPlayerView` des Objekts `scalePolicy` an. Die standardmäßige Skalierungsrichtlinie von `MediaPlayerView` wird mit einer Instanz der Klasse `MaintainAspectRatioScalePolicy` festgelegt. Um die Skalierungsrichtlinie zurückzusetzen, ersetzen Sie die Standardinstanz von `MaintainAspectRatioScalePolicy` auf `MediaPlayerView.scalePolicy` durch Ihre eigene Richtlinie.

>[!IMPORTANT]
>
>Sie können die `scalePolicy`-Eigenschaft nicht auf einen Nullwert setzen.

## Fallback-Szenarien ohne Flash {#non-flash-fallback-scenarios}

Wenn die Skalierungs-Richtlinie in Szenarien ohne Flash ordnungsgemäß funktioniert, muss das Videodiv-Element, das im Konstruktor `View` angegeben wird, für `offsetWidth` und `offsetHeight` Werte ungleich null zurückgeben. Um ein Beispiel für eine fehlerhafte Funktion zu geben, gibt der Konstruktor `View` manchmal null für `offsetWidth` oder `offsetHeight` zurück, wenn die Breite und Höhe der Video-div-Elemente nicht explizit in css festgelegt sind.

>[!NOTE]
>
>Die CustomScalePolicy unterstützt nur wenige Browser, insbesondere IE, Edge und Safari 9. Bei diesen Browsern kann das native Seitenverhältnis des Videos nicht geändert werden. Die Position und die Abmessungen des Videos werden jedoch gemäß der Skalierungsrichtlinie erzwungen.

1. Implementieren Sie die `MediaPlayerViewScalePolicy`-Schnittstelle, um eine eigene Skalierungsrichtlinie zu erstellen.

   Das `MediaPlayerViewScalePolicy` verfügt über eine Methode:

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

1. Weisen Sie Ihre Implementierung der `MediaPlayerView`-Eigenschaft zu.

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. hinzufügen Sie Ihre Ansicht auf die `view`-Eigenschaft des Medienplayers.

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**Beispiel: Skalieren Sie das Video so, dass es die gesamte Ansicht ausfüllt, ohne das Seitenverhältnis beizubehalten:**

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

