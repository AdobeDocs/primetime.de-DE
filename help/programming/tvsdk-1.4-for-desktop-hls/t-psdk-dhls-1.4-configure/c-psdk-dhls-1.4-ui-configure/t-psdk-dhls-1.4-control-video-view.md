---
description: Mit dem MediaPlayerView-Objekt können Sie die Position und Größe der Video-Ansicht steuern.
seo-description: Mit dem MediaPlayerView-Objekt können Sie die Position und Größe der Video-Ansicht steuern.
seo-title: Position und Größe der Video-Ansicht steuern
title: Position und Größe der Video-Ansicht steuern
uuid: 2231c574-03cd-45a8-ab00-4a42f8e044f0
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Position und Größe der Video-Ansicht steuern{#control-the-position-and-size-of-the-video-view}

Mit dem MediaPlayerView-Objekt können Sie die Position und Größe der Video-Ansicht steuern.

TVSDK versucht standardmäßig, das Seitenverhältnis der Video-Ansicht beizubehalten, sobald sich die Größe oder Position des Videos ändert (aufgrund einer Änderung durch die Anwendung, durch einen Profil-Switch oder durch einen Inhaltsschalter usw.).

Sie können das standardmäßige Seitenverhältnis außer Kraft setzen, indem Sie eine andere *Skalierungsrichtlinie* festlegen. Geben Sie die Skalierungsrichtlinie mithilfe der `MediaPlayerView` Objekteigenschaft `scalePolicy` an. Die standardmäßige Skalierungsrichtlinie `MediaPlayerView`wird mit einer Instanz der `MaintainAspectRatioScalePolicy` Klasse festgelegt. Um die Skalierungsrichtlinie zurückzusetzen, ersetzen Sie die Standardinstanz von `MaintainAspectRatioScalePolicy` on `MediaPlayerView.scalePolicy` durch Ihre eigene Richtlinie. (Sie können die `scalePolicy` Eigenschaft nicht auf einen Nullwert setzen.)

1. Implementieren Sie die `MediaPlayerViewScalePolicy` Oberfläche, um eine eigene Skalierungsrichtlinie zu erstellen.

   Die `MediaPlayerViewScalePolicy` Methode hat eine:

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK verwendet ein `StageVideo` Objekt zur Videoanzeige. Da sich `StageVideo` Objekte nicht in der Display-Liste befinden, enthält der `viewPort` Parameter die absoluten Koordinaten des Videos.
   >
   >
   >Beispiel:
   >
   >
   ```
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

1. Weisen Sie Ihre Implementierung der `MediaPlayerView` Eigenschaft zu.

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. hinzufügen Sie Ihre Ansicht auf die `view` Eigenschaft des Medienplayers.

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**Beispiel: Skalieren Sie das Video so, dass es die gesamte Ansicht ausfüllt, ohne das Seitenverhältnis beizubehalten:**

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

