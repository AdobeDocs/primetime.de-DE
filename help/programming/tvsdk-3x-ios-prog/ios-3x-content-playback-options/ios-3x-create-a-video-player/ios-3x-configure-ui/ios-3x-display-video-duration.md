---
description: Sie können die Dauer des derzeit aktiven Inhalts anzeigen.
seo-description: Sie können die Dauer des derzeit aktiven Inhalts anzeigen.
seo-title: Dauer des Videos anzeigen
title: Dauer des Videos anzeigen
uuid: 945f222d-80ba-4832-a06f-9bb8db6adbcb
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Dauer des Videos {#display-the-duration-of-the-video} anzeigen

Sie können die Dauer des derzeit aktiven Inhalts anzeigen.

Implementieren Sie eine Anzeige für die Videodauer mit dem folgenden Beispielcode:

    Die Eigenschaft &quot;PTMediaPlayer&quot;, &quot;[seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange)&quot;, enthält den aktuellen suchbaren Fensterbereich:
    
    * Bei VOD ist dieser Bereich der gesamte VOD-Inhaltsbereich einschließlich Anzeigen.
    * Bei &quot;live/linear&quot;steht dieser Bereich für das suchbare Fenster.
    
    Weitere Informationen zur API finden Sie unter [TVSDK 3.4 for iOS API Reference](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v3/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
