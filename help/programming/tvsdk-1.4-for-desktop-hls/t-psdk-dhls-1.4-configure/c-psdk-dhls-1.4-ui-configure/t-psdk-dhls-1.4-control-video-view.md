---
description: Sie können die Position und Größe der Videoansicht mithilfe des MediaPlayerView -Objekts steuern.
title: Position und Größe der Videoansicht steuern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Position und Größe der Videoansicht steuern{#control-the-position-and-size-of-the-video-view}

Sie können die Position und Größe der Videoansicht mithilfe des MediaPlayerView -Objekts steuern.

TVSDK versucht standardmäßig, das Seitenverhältnis der Videoansicht beizubehalten, sobald sich die Größe oder Position des Videos ändert (aufgrund einer Änderung durch die Anwendung, durch einen Profilwechsel oder durch einen Inhaltswechsel usw.).

Sie können das standardmäßige Seitenverhältnisverhalten außer Kraft setzen, indem Sie eine andere *Skalierungspolitik*. Geben Sie die Skalierungsrichtlinie mithilfe der `MediaPlayerView` -Objekt `scalePolicy` -Eigenschaft. Die `MediaPlayerView`Die standardmäßige Skalierungsrichtlinie wird mit einer Instanz der `MaintainAspectRatioScalePolicy` -Klasse. Um die Skalierungsrichtlinie zurückzusetzen, ersetzen Sie die Standardinstanz von `MaintainAspectRatioScalePolicy` on `MediaPlayerView.scalePolicy` mit Ihrer eigenen Richtlinie. (Sie können die Variable `scalePolicy` -Eigenschaft auf einen Nullwert gesetzt.)

1. Implementieren des `MediaPlayerViewScalePolicy` -Schnittstelle, um eine eigene Skalierungsrichtlinie zu erstellen.

   Die `MediaPlayerViewScalePolicy` verfügt über eine Methode:

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK verwendet eine `StageVideo` -Objekt zum Anzeigen des Videos und weil `StageVideo` -Objekte sich nicht in der Anzeigeliste befinden, wird die `viewPort` enthält die absoluten Koordinaten des Videos.
   >
   >
   >Beispiel:
   >
   >```
   >public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
   >       /** 
   >         * Default constructor. 
   >         */ 
   >       public function CustomScalePolicy() { 
   >       } 
   > 
   >    
      public function adjust(viewPort:Rectangle,  
   >                                                     videoWidth:Number,  
   >                                                     videoHeight:Number):Rectangle { 
   >               return customAdjustment(); 
   >       } 
   > 
   >    
      public function customAdjustment():Rectangle { 
   >               /* Your custom adjustment here */ 
   >               [...] 
   >       } 
   >}
   >```
   >

1. Weisen Sie Ihre Implementierung dem `MediaPlayerView` -Eigenschaft.

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. Hinzufügen Ihrer Ansicht zum Medienplayer `view` -Eigenschaft.

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**Beispiel: Skalieren Sie das Video, um die gesamte Videoansicht auszufüllen, ohne das Seitenverhältnis beizubehalten:**

```
package com.adobe.mediacore.samples.utils { 
    import com.adobe.mediacore.view.MediaPlayerViewScalePolicy; 
    import flash.geom.Rectangle; 
 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
 
        /** 
        * Default constructor. 
        */ 
        public function CustomScalePolicy() { 
        } 
 
        public function adjust(viewPort:Rectangle, 
                               videoWidth:Number,  
                               videoHeight:Number):Rectangle { 
            return viewPort; 
        } 
    } 
} 
 
var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
view.scalePolicy = new CustomScalePolicy(); 
addChild(view); 
mediaPlayer.view = view;
```
