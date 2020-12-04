---
description: Sie können die Dauer des derzeit aktiven Inhalts anzeigen.
seo-description: Sie können die Dauer des derzeit aktiven Inhalts anzeigen.
seo-title: Dauer des Videos anzeigen
title: Dauer des Videos anzeigen
uuid: 02042070-9c55-4cbb-9dc1-49987451eb8f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Dauer des Videos {#display-the-duration-of-the-video} anzeigen

Sie können die Dauer des derzeit aktiven Inhalts anzeigen.

Implementieren Sie eine Anzeige für die Videodauer mit dem folgenden Beispielcode:

    Die Eigenschaft &quot;PTMediaPlayer&quot;, [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange), enthält den aktuellen suchbaren Fensterbereich:
    
    * Bei VOD ist dieser Bereich der gesamte VOD-Inhaltsbereich einschließlich Anzeigen.
    * Bei &quot;live/linear&quot;steht dieser Bereich für das suchbare Fenster.
    
    Weitere Informationen zur API finden Sie unter [TVSDK 1.4 for iOS API Reference](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
