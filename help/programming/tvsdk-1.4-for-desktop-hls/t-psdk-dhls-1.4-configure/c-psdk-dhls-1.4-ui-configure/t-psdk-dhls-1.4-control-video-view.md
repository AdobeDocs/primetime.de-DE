---
description: Mit dem MediaPlayerView-Objekt können Sie die Position und Größe der Video-Ansicht steuern.
title: Position und Größe der Video-Ansicht steuern
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Position und Größe der Video-Ansicht kontrollieren{#control-the-position-and-size-of-the-video-view}

Mit dem MediaPlayerView-Objekt können Sie die Position und Größe der Video-Ansicht steuern.

TVSDK versucht standardmäßig, das Seitenverhältnis der Video-Ansicht beizubehalten, sobald sich die Größe oder Position des Videos ändert (aufgrund einer Änderung durch die Anwendung, durch einen Profil-Switch oder durch einen Inhaltsschalter usw.).

Sie können das standardmäßige Seitenverhältnis außer Kraft setzen, indem Sie eine andere *Skalierungsrichtlinie* angeben. Geben Sie die Skalierungsrichtlinie mit der Eigenschaft `MediaPlayerView` des Objekts `scalePolicy` an. Die standardmäßige Skalierungsrichtlinie von `MediaPlayerView` wird mit einer Instanz der Klasse `MaintainAspectRatioScalePolicy` festgelegt. Um die Skalierungsrichtlinie zurückzusetzen, ersetzen Sie die Standardinstanz von `MaintainAspectRatioScalePolicy` auf `MediaPlayerView.scalePolicy` durch Ihre eigene Richtlinie. (Die `scalePolicy`-Eigenschaft kann nicht auf einen Nullwert gesetzt werden.)

1. Implementieren Sie die `MediaPlayerViewScalePolicy`-Schnittstelle, um eine eigene Skalierungsrichtlinie zu erstellen.

   Das `MediaPlayerViewScalePolicy` verfügt über eine Methode:

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK verwendet ein `StageVideo`-Objekt zum Anzeigen des Videos. Da sich `StageVideo`-Objekte nicht in der Display-Liste befinden, enthält der `viewPort`-Parameter die absoluten Koordinaten des Videos.
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

1. Weisen Sie Ihre Implementierung der `MediaPlayerView`-Eigenschaft zu.

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. hinzufügen Sie Ihre Ansicht auf die `view`-Eigenschaft des Medienplayers.

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

